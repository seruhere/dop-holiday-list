# India Post Holiday Calendar

Interactive calendar for **India Post gazetted holidays** — built from [indiapost.gov.in/holidays-list](https://www.indiapost.gov.in/holidays-list) and the official West Bengal Circle 2026 calendar (`West_Bengal_Holidays_2026.jpg`).

Open `holiday_calendar.html` in any modern browser — no build step, no server required.

## Demo
- **Primary file:** `holiday_calendar.html` (single-file, offline)
- **Backup:** `holiday_calendar_v2.html` (identical)

Just double-click to open.

## Features

- **Year + State/Circle selectors** — 2025–2026 (easily extended). All postal circles (All India, West Bengal, Sikkim, Andaman & Nicobar, Delhi, Maharashtra … 31 options) — `holiday_calendar.html:307`
- **17 gazetted holidays everywhere** — fixed at `holiday_calendar.html:394` / `holiday_calendar.html:526`. `All India` + every circle now returns 17 (Basant Panchami, Holi, Maha Ashtami + 14 standard). Source: 14 from India Post site + 3 state extras from the West Bengal image.
- **Single month view + slider** — current month visible on load (`currentMonth = new Date().getMonth()` at `holiday_calendar.html:489`). Drag `<input type="range" id="monthSlider">` or `‹ / ›` buttons to change month/year — `holiday_calendar.html:281` / `holiday_calendar.html:342`
- **Stats bar** — `Total / Crossed / Left / Long Weekends` computed per year+state at `holiday_calendar.html:535/549`
  - `Crossed` = `h.date < today`
  - `Long Weekend` = holiday on **Monday (1) or Saturday (6)** at `holiday_calendar.html:530`
- **Complete holiday list** — full-year sorted list below calendar at `holiday_calendar.html:343` (not just “this month”), with `This Month` + `Long Weekend` badges, past items faded.
- **Smaller, rounded days** — `holiday_calendar.html:134` `.day { aspect-ratio:1; border-radius:10px; padding:4px; font-size:0.82rem; justify-content:center }` with centered `30×30px` day number at `holiday_calendar.html:151` (`font-size:0.88rem`).
- **Holiday highlight `#f2aaaa`** — `holiday_calendar.html:169` `.day.holiday, .day.sunday { background:#f2aaaa }` and legend at `holiday_calendar.html:287`; hover `#e89898`, today outline `#0056a0`, Sundays light-red.
- **Dark / Light mode** — toggle `🌙 Dark / ☀️ Light` at `holiday_calendar.html:310` (`#themeToggle`), persisted in `localStorage('holiday-theme')` at `holiday_calendar.html:735`, styles at `holiday_calendar.html:268`
- **Tooltip + responsive** — hover a red day to see names (`#tooltip` at `holiday_calendar.html:189`), grids collapse `4→3→2→1` columns.

## Data

Source verified 12 Aug 2026:

| # | Holiday | 2026 Date | Day |
|---|---------|-----------|-----|
| 01 | Basant Panchami / Sri Panchami | 23 Jan 2026 | Friday |
| 02 | Republic Day | 26 Jan 2026 | Monday |
| 03 | Holi | 04 Mar 2026 | Wednesday |
| 04 | Id-ul-Fitr | 21 Mar 2026 | Saturday |
| 05 | Mahavir Jayanti | 31 Mar 2026 | Tuesday |
| 06 | Good Friday | 03 Apr 2026 | Friday |
| 07 | Buddha Purnima | 01 May 2026 | Friday |
| 08 | Id-ul-Zuha (Bakrid) | 27 May 2026 | Wednesday |
| 09 | Muharram | 26 Jun 2026 | Friday |
| 10 | Independence Day | 15 Aug 2026 | Saturday |
| 11 | Milad-un-Nabi / Id-E-Milad | 26 Aug 2026 | Wednesday |
| 12 | Mahatma Gandhi's Birthday | 02 Oct 2026 | Friday |
| 13 | Dussehra (Maha Ashtami) | 19 Oct 2026 | Monday |
| 14 | Dussehra | 20 Oct 2026 | Tuesday |
| 15 | Diwali (Deepavali) | 08 Nov 2026 | Sunday |
| 16 | Guru Nanak's Birthday | 24 Nov 2026 | Tuesday |
| 17 | Christmas Day | 25 Dec 2026 | Friday |

2025 set at `holiday_calendar.html:454` (Holi 14-Mar-2025, Basant 02-Feb-2025, Maha Ashtami 01-Oct-2025 etc.). Add/override per circle in `HOLIDAYS` object — e.g.:
```js
HOLIDAYS['maharashtra'] = { 2026: [ {name:"Holi", date:"2026-03-04"}, ... ] }
```

## Usage

1. **Open** `holiday_calendar.html`
2. **Pick Year** and **State / Circle**
3. **Slide** month or use `‹ ›` — calendar updates, `Total / Left / Long Weekend` stays per-year
4. **Click** a day for tooltip; list highlights “This Month” items
5. **Toggle** 🌙/☀️ for dark mode (saved automatically)

No dependencies — pure HTML/CSS/vanilla JS.

## File Structure

```
holiday_calendar.html      # main app (single file)
holiday_calendar_v2.html   # identical backup
West_Bengal_Holidays_2026.jpg/.png  # source image for 17
README.md                  # this file
```

## Customization

- **Add year:** extend `initSelectors()` range at `holiday_calendar.html:496` and add entry in `HOLIDAYS`
- **Per-state overrides:** edit `HOLIDAYS[state][year]`; the `STATES.forEach` fallback at `holiday_calendar.html:528` auto-fills 17 for any unconfigured circle
- **Colors:** change `#f2aaaa` at `holiday_calendar.html:169`, `#0056a0` primary, `#f0f2f5` page bg at `holiday_calendar.html:9`
- **Day size:** `.day`/` .day-number` at `holiday_calendar.html:134/151`

## Verification

- Cross-checked `indiapost.gov.in/holidays-list` (All India 14) + `West_Bengal_Holidays_2026.jpg` (17) — see `WEST_BENGAL_2026` at `holiday_calendar.html:394`
- Long weekends computed via `getDay() === 1 || 6`
- Tested on Chrome/Firefox/Edge, mobile (580px single column)

## License

Data © Department of Posts, Ministry of Communications, GoI. Code MIT — use freely, verify holidays with your local post office for branch closures.
