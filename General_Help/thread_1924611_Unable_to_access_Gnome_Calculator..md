---
title: "Unable to access Gnome Calculator."
date: 2012-02-13
forum: General Help
---

### Post by naikaniket.23 on 2012-02-13
I am unable to access Inbuilt  calculator. After running the command nothing happens. what to do? I tried uninstalling & Installing again still no luck.


I tried running command in the Terminal the output was,

[SIZE="2"][COLOR="Red"]"$ gcalc
No command 'gcalc' found, did you mean:
 Command 'wcalc' from package 'wcalc' (universe)
 Command 'calc' from package 'apcalc' (universe)
 Command 'xcalc' from package 'x11-apps' (main)
 Command 'lcalc' from package 'lcalc' (universe)
 Command 'rcalc' from package 'radiance' (universe)
 Command 'gcal' from package 'gcal' (universe)
 Command 'kcalc' from package 'kcalc' (main)
 Command 'icalc' from package 'radiance' (universe)
gcalc: command not found"[/COLOR][/SIZE]


Please Help me.

---

### Post by dcstar on 2012-02-13
> **naikaniket.23 said:**
> I am unable to access Inbuilt  calculator. After running the command nothing happens. what to do? I tried uninstalling & Installing again still no luck.


I tried running command in the Terminal the output was,

[SIZE="2"][COLOR="Red"]"$ gcalc
No command 'gcalc' found, did you mean:
 Command 'wcalc' from package 'wcalc' (universe)
 Command 'calc' from package 'apcalc' (universe)
 Command 'xcalc' from package 'x11-apps' (main)
 Command 'lcalc' from package 'lcalc' (universe)
 Command 'rcalc' from package 'radiance' (universe)
 Command 'gcal' from package 'gcal' (universe)
 Command 'kcalc' from package 'kcalc' (main)
 Command 'icalc' from package 'radiance' (universe)
gcalc: command not found"[/COLOR][/SIZE]


Please Help me.

```
gcalctool
```

---

### Post by naikaniket.23 on 2012-02-13
> **dcstar said:**
> ```
gcalctool
```
Thanks DCSTAR, I tried the command the output was 

"[COLOR="Red"]$ gcalctool
** (gcalctool:2007): DEBUG: Using IMF rate of 0.8534360000 for EUR
** (gcalctool:2007): DEBUG: Using IMF rate of 0.0083552700 for JPY
** (gcalctool:2007): DEBUG: Using IMF rate of 1.0208600000 for GBP
** (gcalctool:2007): DEBUG: Using IMF rate of 0.6429380000 for USD
** (gcalctool:2007): DEBUG: Using IMF rate of 0.0086204400 for DZD
** (gcalctool:2007): DEBUG: Using IMF rate of 0.6962300000 for AUD
** (gcalctool:2007): DEBUG: Using IMF rate of 1.7180100000 for BHD
** (gcalctool:2007): DEBUG: Using IMF rate of 0.0898548000 for BWP
** (gcalctool:2007): DEBUG: Using IMF rate of 0.3744990000 for BRL
** (gcalctool:2007): DEBUG: Using IMF rate of 0.5175650000 for BND
** (gcalctool:2007): DEBUG: Using IMF rate of 0.6493500000 for CAD
** (gcalctool:2007): DEBUG: Using IMF rate of 0.0013427300 for CLP
** (gcalctool:2007): DEBUG: Using IMF rate of 0.1023470000 for CNY
** (gcalctool:2007): DEBUG: Using IMF rate of 0.0003612910 for COP
** (gcalctool:2007): DEBUG: Using IMF rate of 0.0338738000 for CZK
** (gcalctool:2007): DEBUG: Using IMF rate of 0.1139500000 for DKK
** (gcalctool:2007): DEBUG: Using IMF rate of 0.0029121500 for HUF
** (gcalctool:2007): DEBUG: Using IMF rate of 0.0052488300 for ISK
** (gcalctool:2007): DEBUG: Using IMF rate of 0.0132047000 for INR
** (gcalctool:2007): DEBUG: Using IMF rate of 0.0000717907 for IDR
** (gcalctool:2007): DEBUG: Using IMF rate of 0.0000526895 for IRR
** (gcalctool:2007): DEBUG: Using IMF rate of 0.1730900000 for ILS
** (gcalctool:2007): DEBUG: Using IMF rate of 0.0043453000 for KZT
** (gcalctool:2007): DEBUG: Using IMF rate of 0.0005768130 for KRW
** (gcalctool:2007): DEBUG: Using IMF rate of 2.3269900000 for KWD
** (gcalctool:2007): DEBUG: Using IMF rate of 0.5174910000 for LYD
** (gcalctool:2007): DEBUG: Using IMF rate of 0.2133210000 for MYR
** (gcalctool:2007): DEBUG: Using IMF rate of 0.0222580000 for MUR
** (gcalctool:2007): DEBUG: Using IMF rate of 0.0510764000 for MXN
** (gcalctool:2007): DEBUG: Using IMF rate of 0.0082342000 for NPR
** (gcalctool:2007): DEBUG: Using IMF rate of 0.5387410000 for NZD
** (gcalctool:2007): DEBUG: Using IMF rate of 0.1111270000 for NOK
** (gcalctool:2007): DEBUG: Using IMF rate of 1.6800300000 for OMR
** (gcalctool:2007): DEBUG: Using IMF rate of 0.0071228300 for PKR
** (gcalctool:2007): DEBUG: Using IMF rate of 0.2397930000\u000d for PEN
** (gcalctool:2007): DEBUG: Using IMF rate of 0.0151447000 for PHP
** (gcalctool:2007): DEBUG: Using IMF rate of 0.2030980000 for PLN
** (gcalctool:2007): DEBUG: Using IMF rate of 0.1774650000 for QAR
** (gcalctool:2007): DEBUG: Using IMF rate of 0.0214701000 for RUB
** (gcalctool:2007): DEBUG: Using IMF rate of 0.1722590000 for SAR
** (gcalctool:2007): DEBUG: Using IMF rate of 0.5175650000 for SGD
** (gcalctool:2007): DEBUG: Using IMF rate of 0.0850832000 for ZAR
** (gcalctool:2007): DEBUG: Using IMF rate of 0.0056738100 for LKR
** (gcalctool:2007): DEBUG: Using IMF rate of 0.0961727000 for SEK
** (gcalctool:2007): DEBUG: Using IMF rate of 0.7020680000 for CHF
** (gcalctool:2007): DEBUG: Using IMF rate of 0.0208782000 for THB
** (gcalctool:2007): DEBUG: Using IMF rate of 0.1011850000 for TTD
** (gcalctool:2007): DEBUG: Using IMF rate of 0.4277400000 for TND
** (gcalctool:2007): DEBUG: Using IMF rate of 0.1758950000 for AED
** (gcalctool:2007): DEBUG: Using IMF rate of 0.0330944000\u000d for UYU
** (gcalctool:2007): DEBUG: Using IMF rate of 0.1506010000 for VEF
** (gcalctool:2007): DEBUG: Using ECB fixed rate of 0.06391 for EEK
/home/     /.cache/gcalctool/eurofxref-daily.xml:30: parser error : Specification mandate value for attribute rate
			<Cube currency='HKD' rate
			                         ^
/home/    /.cache/gcalctool/eurofxref-daily.xml:30: parser error : attributes construct error
			<Cube currency='HKD' rate
			                         ^
/home/   /.cache/gcalctool/eurofxref-daily.xml:30: parser error : Couldn't find end of Start Tag Cube line 30
			<Cube currency='HKD' rate
			                         ^
/home/  /.cache/gcalctool/eurofxref-daily.xml:30: parser error : Premature end of data in tag Cube line 8
			<Cube currency='HKD' rate
			                         ^
/home/    /.cache/gcalctool/eurofxref-daily.xml:30: parser error : Premature end of data in tag Cube line 7
			<Cube currency='HKD' rate
			                         ^
/home/     /.cache/gcalctool/eurofxref-daily.xml:30: parser error : Premature end of data in tag Envelope line 2
			<Cube currency='HKD' rate
			                         ^

** ERROR **: Couldn't parse ECB rate file H\xf4\xd6
aborting...
Aborted"
[/COLOR]

I am unable to understand the problem please help.

---

### Post by jsstn on 2012-02-13
if you are not planning on using the calculator to do currency conversions, you can try removing the file $HOME/.cache/gcalctool/eurofxref-daily.xml (and maybe other files in .cache/gcalctool, but keep them somewhere else as backup).
if that doesn't work and you don't need the gui of gnome calculator, you can try using the command ```
gcalccmd
``` from the command line.

---

