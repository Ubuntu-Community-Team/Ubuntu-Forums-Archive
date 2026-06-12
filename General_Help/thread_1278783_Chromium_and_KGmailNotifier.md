---
title: "Chromium and KGmailNotifier"
date: 2009-09-29
forum: General Help
---

### Post by Stosskraft on 2009-09-29
Hello all,

I have recently installed Chromium browsers through tweak. I am trying to get it recognized as the default browser for ubuntu. During the set up I clicked "make chromium your default browser" and then I went to System-Preferences-Preferred Applications and changed the Web Browser to Chromium and then under Mail Reader I changed it to Custom with the command line: "gmail %s"

Now in KGmailNotifier I changed the Path to Browser from: "/usr/bin/firefox" to "/usr/bin/chromium" to have Chromium open when I click the KGmailNotifier icon on the tray but it is not working.

I know Chromium still have some bugs, is this one of them? I can get it to open my email with firefox but I would like it to with chromium.

Can anyone tell me how to find the path to my chromium file? is this were I am making the mistake in the path name?

Thank you all

---

### Post by rifak on 2009-09-30
the command to open chromium is:
```
chromium-browser
```

try using this for the command in kGMailNotify
```
/usr/bin/chromium-browser
```

that should work

---

### Post by Stosskraft on 2009-09-30
Hey Thanks, Problem solved.

I right clicked on the Chromium tab and used the command line I saw there "chromium-browser".

Thanks for the help, I was having trouble with CheckGmail as I could not log in, so I will work with KGmailNotifier it seems to do the job.

Thanks again

---

### Post by Stosskraft on 2009-09-30
Hello, could someone give me the command to enter in the start-up menu?

How do you get this command? I tried "which KGmailNotifier" in the terminal but nothing happen.

Thanks

---

### Post by Stosskraft on 2009-10-01
bump

---

