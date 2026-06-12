---
title: "Chromium doesn't render Japanese fonts properly"
date: 2010-10-10
forum: General Help
---

### Post by HangukMiguk on 2010-10-10
So far, as a former Chrome user on Windows, I am enjoying Chromium.  However, there is one glaring problem that is bugging me, and is disrupting my usage of the browser.

Chromium will not show Japanese fonts properly.  It's not that everything shows up as boxes.  The problem is that certain characters will show in Japanese, and certain will show in Korean, thereby making the Japanese text unreadable.  Copying and pasting into gedit allows me to read the Japanese text, and Firefox never had this problem, however, within Chromium, this is unreadable.

Here is a picture to show you what I mean:

[img]http://img412.imageshack.us/img412/4814/chromiumerror.jpg[/img]

Has anyone else had this problem, and fixed it?  I have installed the language packs and have tried setting things to different unicode fonts and changing the encoding to unicode and even Japanese, and continue to get these errors.

---

### Post by HangukMiguk on 2010-10-11
Bump, really needing this fixed.

---

### Post by sendblink23 on 2010-10-11
Do other browsers do the same? If they do... then its a bug on the OS, but if on other browsers you don't see that issue... then its a bug on Chromium

Post back... what can you find - hopefully some GURU comes here and helps you out - that sure needs fixing


***********update
woops my bad... didn't see you did mention using Firefox you didn't have any problems
Then its a Chromium issue.. you will have top report a bug on launchpad

---

### Post by HangukMiguk on 2010-10-11
Thanks, just posted up a bug report.  Hopefully this gets fixed.

---

### Post by kumaryu on 2010-10-11
Have you added the  repositories from "Ubuntu Japanese team" to your sources? Shift-JIS is the defacto standard for Japanese encodings. The "Japanese Team" repositories provide improved support for rendering mixed character sets with Shift-JIS, ISO-2022-JP and EUC-JP in addition to UTF-8.

Different reps apply to different Ubuntu releases. Instructions for adding GPG key and the repositories are provided here:

[http://www.ubuntulinux.jp/products/JA-Localized](http://www.ubuntulinux.jp/products/JA-Localized)

The page is in Japanese but the commands and the OS version they apply to should not be difficult to figure out. 

(It should be noted that these changes don't interact well with other (non Japanese) character sets. If you already have it installed in addition to character sets for other languages (Korean, for example) then try without.)


I'm using Maverick (10.10 upgraded from Lucid), Chromium 6.0.472.63 (59945) as well as Chrome 7.0.517.36 beta. I don't have the font rendering issue that you describe so I don't think the issue is endemic to Maverick/Chromium.

---

