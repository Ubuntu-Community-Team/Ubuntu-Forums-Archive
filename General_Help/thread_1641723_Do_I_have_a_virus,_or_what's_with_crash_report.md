---
title: "Do I have a virus, or what's with crash report?"
date: 2010-12-09
forum: General Help
---

### Post by cagliostro on 2010-12-09
Happily using Karmic Koala, and Firefox 3.5.3. When go online, the header in Firefox shows an orange splat icon with exclamation point. Click on this for "Crash report detected." But there is no crash. It says: "Please enter you password to access problem report of system programs."

I'm used to entering an administrative password to change things. Why would I need to enter my password just to view a report? That doesn't make sense. And there is no crash. I won't do it. I know Linux isn't supposed to have viruses, but still....

I know exactly when this started. Never had a problem until a few days ago. From a Tomb Raider gaming site, I was directed to a link for a Windows XP patch, to speed up playing a custom level. This was a suspicious site--all kinds of "download" buttons that weren't for downloading the program at all. Then it wasn't a zip file, but an exe. I deleted it, never transferred the patch to my Windows gaming computer. (I only go online using Linux.) Then next day this link was dropped, because it turned out to be a suspected virus site. I started to see this orange icon in the Firefox header, click on it, and "Please enter your password..."

Am I crazy to be paranoid about this?

---

### Post by Rubi1200 on 2010-12-09
First things first,
delete the cache and all cookies in Firefox and then restart and see if the problem persists.

I would also recommend looking in the system logs for any suspicious errors.

System > Administration > Log File Viewer

Of particular interest would be the auth.log, syslog, and messages.

I also recommend you install the NoScript addon for Firefox:
[https://addons.mozilla.org/en-US/firefox/addon/722/](https://addons.mozilla.org/en-US/firefox/addon/722/)

---

### Post by cagliostro on 2010-12-09
Thank you for your response. I have installed the NoScript addon of your link, and running it. Problem persists.

Firefox cache already deleted. Cookies restored to day one (I wrote a desktop script to return cookies to essentials, I overwrite active file with a saved copy).

The log files are a bit beyond me, but nothing stands out as suspicious. Not sure that I know what to look for.

Shut down the computer. Restart, start up improved Firefox with addon. I go to the site [www.trle.net](www.trle.net), which is devoted to Tomb Raider custom levels. The orange icon, with exclamation point, shows up in the Firefox header.

---

### Post by bodhi.zazen on 2010-12-09
> **cagliostro said:**
> Am I crazy to be paranoid about this?

Yes. This is not Windows and I have yet to see a crash or automated crash report caused by malware on Linux.

Run firefox from the command line and see what error messages you get.

Run the crash report and see what it is telling you.

If all else fails, delete your firefox profile and start again.

---

### Post by cagliostro on 2010-12-10
Okay, the crash report has to do with a kernel panic, and about reporting this to Ubuntu developers. Thank you.

So this is solved, but....

The orange icon never appeared when I started or worked on this computer. It never showed up when I started Firefox on my home page. It only appeared when I started to browse with Firefox online (over a dozen occurrences). All the crash report did was ask if I wanted to report the incident to Ubuntu. Seems odd I was forced to enter a password. A log file seems to show attempts to run sudo, which failed without my password.

The icon is gone, my computer works fine. I reserved extra spare partitions, so I may upgrade just in case.

---

### Post by tredegar on 2010-12-10
> A log file seems to show attempts to run sudo, which failed without my password.

The icon is gone, my computer works fine. 

If I were you, I'd change my password _right now_.

---

### Post by cagliostro on 2010-12-10
Good idea. Password changed.

---

### Post by Rubi1200 on 2010-12-10
Are you running any server software or remote desktop/file sharing programs?

Please copy/past the relevant portions of the log with the failed sudo attempts and get it back here for us to look at.

Thanks.

---

### Post by cagliostro on 2010-12-10
Thanks. I really don't think it's anything; the problem is solved.

Had some readings like this yesterday--

david-laptop sudo: pam_unix(sudo:auth): auth could not identify password for [david]

but on second thought, I believe that I provoked that trying to get rid of the orange crash-report icon. Not running any server software or anything. I had never seen a crash report before--an indication of how solid Ubuntu is--and the way it appeared when I went online simply puzzled me.

---

### Post by bodhi.zazen on 2010-12-10
> **cagliostro said:**
> Thanks. I really don't think it's anything; the problem is solved.

Had some readings like this yesterday--

david-laptop sudo: pam_unix(sudo:auth): auth could not identify password for [david]

but on second thought, I believe that I provoked that trying to get rid of the orange crash-report icon. Not running any server software or anything. I had never seen a crash report before--an indication of how solid Ubuntu is--and the way it appeared when I went online simply puzzled me.

Always nice to see people recover from insanity.

---

### Post by Swagman on 2010-12-10
Yeah.. He's got a Cerstificate that says he's sane... I haven't !!

Wait..What ?

:D

To quote Helen Reddy 

"It's so nice to be insane.. No-one asks you to explain"

I don't suffer from insanity.. I enjoy it !!

---

