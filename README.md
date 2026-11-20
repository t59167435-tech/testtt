# Discipline: offline habit tracker with local reminders

Everything lives on the phone. No server, no account, no internet needed.

## What it does
- Daily checklist with a live percentage score and a final result at the end of the day
- Locked items (10 PM for the "did not" items, 8 PM for fruits), a countdown study timer, and a Yes/No gym-time question
- Calendar: green / yellow / red days, tap a date for its full report
- Stats: daily bars, weekly list, monthly list, all-time average, per-habit success rates
- Streaks (overall and per habit) and personal records
- Reminders scheduled locally on the phone: every N hours, morning, evening, missed-task, custom messages, sound and vibration toggles

## Get it on your phone (Android, no Android Studio needed)
1. Create a free GitHub account and a new empty repository.
2. Upload everything in this folder (keep the `.github` folder) to the repository's `main` branch.
3. Open the repository's **Actions** tab. The "Build Android APK" workflow runs by itself (about 5 minutes).
4. Open the finished run, download the **discipline-apk** artifact, unzip it, and send `app-debug.apk` to your phone.
5. Install it (allow "install unknown apps" when asked) and open the app.
6. When asked, **allow notifications**. If your phone asks about "alarms & reminders", allow that too.
7. Open **Settings → Notifications → Save and schedule** once to confirm the reminders are set.

## Or build with Android Studio
```
npm install
npx cap add android
npx cap sync android
npx cap open android
```
Then press Run. Add these permissions to `android/app/src/main/AndroidManifest.xml` if they are missing:
`POST_NOTIFICATIONS`, `SCHEDULE_EXACT_ALARM`, `RECEIVE_BOOT_COMPLETED`, `VIBRATE`.

## Reminders: things worth knowing
- Reminders repeat daily at fixed times and are re-scheduled every time you open the app or save settings.
- Message text rotates through your list, one per time slot. The text is fixed when scheduled, so it cannot say "you have 4 tasks left" automatically.
- Some phone brands (Tecno, Infinix, Xiaomi, Oppo, Samsung) kill background apps. If reminders stop, set the app's battery usage to **Unrestricted** and allow **Autostart** if your phone has it.
- Sound and vibration changes apply when you press **Save and schedule**.
- iPhone: needs a Mac with Xcode (`npx cap add ios`). Android is the easy path.

## Backup
Data is stored only on the phone. Use **Settings → Backup → Copy backup** and paste it somewhere safe now and then. Uninstalling the app erases the data.

## Edit the habits
Open `www/index.html` and change the `HABITS` list near the top, or add and hide habits inside the app under Settings.
