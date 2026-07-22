<wizard-report>
# PostHog post-wizard report

<!-- sourcebound:role evidence -->

**Snapshot:** repository commit `385e9e1287cc55d004883e22e7a73e8716ff6668`, inspected
2026-07-21.

The wizard configured PostHog in this Next.js 15 SaaS Starter. Client capture starts in
`instrumentation-client.ts`, with a reverse proxy in `next.config.ts`. The server client in
`lib/posthog-server.ts` captures events from Server Actions and API routes. Sign-in, sign-up, and
dashboard loading identify the same database user ID on both sides. The client enables error
tracking with `capture_exceptions: true`.

| Event | Description | File |
|---|---|---|
| `user_signed_in` | User successfully signs in | `app/(login)/actions.ts` |
| `user_signed_up` | New user completes registration | `app/(login)/actions.ts` |
| `user_signed_out` | User signs out | `app/(login)/actions.ts` |
| `invitation_accepted` | User signs up via an invitation link | `app/(login)/actions.ts` |
| `password_updated` | User changes their password | `app/(login)/actions.ts` |
| `account_updated` | User updates their name or email | `app/(login)/actions.ts` |
| `account_deleted` | User deletes their account (churn signal) | `app/(login)/actions.ts` |
| `team_member_invited` | Team owner sends a new member invitation | `app/(login)/actions.ts` |
| `team_member_removed` | Team owner removes a member | `app/(login)/actions.ts` |
| `checkout_initiated` | User starts the Stripe checkout flow | `lib/payments/actions.ts` |
| `checkout_completed` | Stripe checkout succeeds and subscription is saved | `app/api/stripe/checkout/route.ts` |
| `subscription_updated` | Stripe webhook signals a subscription change | `app/api/stripe/webhook/route.ts` |
| `subscription_canceled` | Stripe webhook signals a subscription cancellation | `app/api/stripe/webhook/route.ts` |
| `customer_portal_opened` | User opens the Stripe billing portal | `lib/payments/actions.ts` |

## Next steps

We've built some insights and a dashboard for you to keep an eye on user behavior, based on the events we just instrumented:

- **Dashboard — Analytics basics**: https://us.posthog.com/project/228144/dashboard/1468191
- **Signup → Checkout Conversion Funnel**: https://us.posthog.com/project/228144/insights/Rejsc2sS
- **New Sign-ups Over Time**: https://us.posthog.com/project/228144/insights/pjba3GRc
- **Account Deletions (Churn)**: https://us.posthog.com/project/228144/insights/uW9rQTkw
- **Subscription Events** (completed vs canceled): https://us.posthog.com/project/228144/insights/vm180PKL
- **Daily Active Users (Sign-ins)**: https://us.posthog.com/project/228144/insights/5gDwVemn

### Agent skill

The generated agent skill records the integration context for later maintenance. Treat this report
as a snapshot; verify current setup against the listed files before changing it.

</wizard-report>
