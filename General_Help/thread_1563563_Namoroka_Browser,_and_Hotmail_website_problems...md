---
title: "Namoroka Browser, and Hotmail website problems.."
date: 2010-08-29
forum: General Help
---

### Post by liviococcia on 2010-08-29
Hello Members.
I was using the latest stable Firefox, and found that when i logged into my Hotmail account, the page would load but you couldn't open emails, or open any of the account folders, even though everything displays correctly,there were no page errors reported when the web-page loading was completed.

I then thought i give Firefox beta version 'Namoroka' a try, but i still get the same issue, although sometimes the Hotmail page works correctly surprisingly.

On the rare occasion when it works, if i click onto an email, or folder, a little yellow box in the bottom right corner appears with the word 'Loading...', so what ever this thing is that needs to be started up when you log into Hotmail for some reason doesn't startup.

If i use Google Chromium browser, which does happen to be on Ubuntu's daily build updates service, so i suppose is again a beta version, always works with regards to the Hotmail web-site, and accessing my account.

I know there are issues at the moment regarding the Hotmail service, with people having various problems on various forums, but my Namoroka browser just shows no sign of being rectified, i have posted this issue on Mozilla's beta forum.

Is anyone encountering this same problem, and maybe know of a solution or workaround.

Kind regards
Livio

---

### Post by lovinglinux on 2010-08-29
Have you tried to start Firefox in safe mode?

Have you tried to create a new Firefox profile?

Have you tried Firefox 4.0b4?

See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

### Post by liviococcia on 2010-08-30
> **lovinglinux said:**
> Have you tried to start Firefox in safe mode?

Have you tried to create a new Firefox profile?

Have you tried Firefox 4.0b4?

See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.
Thanks lovinglinux for the help.

Just to say 'no' i haven't to the first suggestion, to your second i'm not sure how you create a new Firefox profile i'm still a novice user, and 'no' i haven't tried Firefox 4 beta, if i did would it install over the top of the Namoroka (Firefox beta) browser that i have already, or would it be a completely separate installation?

thanks again, regards

---

### Post by lovinglinux on 2010-08-30
> **liviococcia said:**
> Thanks lovinglinux for the help.

Just to say 'no' i haven't to the first suggestion, to your second i'm not sure how you create a new Firefox profile i'm still a novice user, and 'no' i haven't tried Firefox 4 beta, if i did would it install over the top of the Namoroka (Firefox beta) browser that i have already, or would it be a completely separate installation?

thanks again, regards

See the tutorial link in my first post. It has instructions on how to create a new profile and other methods of troubleshooting Firefox.

Firefox 4 is currently installed side-by-side with 3.6 and it makes a copy of your user profile, if you install from the repository that you already have. Nevertheless, you can also download it from Mozilla and install manually. See [http://ubuntuforums.org/showthread.php?t=1544124](http://ubuntuforums.org/showthread.php?t=1544124)

---

### Post by liviococcia on 2010-08-31
Thanks again lovinglinux for all the help, i followed the help from the link you posted and so far Hotmail seems to be working again, i think i'll stay with Namoroka beta for a bit longer and then i'll give Firefox 4 a go.

kind regards
Livio

---

### Post by malibusurfer2 on 2010-09-20
Type in about:config in the address bar of Namoroka.
Filter (search) for: user:agent.
Double click on: general.useragent.extra.firefox.
Change Namoroka to Firefox.
You can leave the /version info stuff.

---

### Post by liviococcia on 2010-09-21
> **malibusurfer2 said:**
> Type in about:config in the address bar of Namoroka.
Filter (search) for: user:agent.
Double click on: general.useragent.extra.firefox.
Change Namoroka to Firefox.
You can leave the /version info stuff.
Thanks malibusurfer2, I have done this but it hasn't resolved my problems, incredibly, using either the latest stable Firefox or Firefox 4 produces the same problems also, regardless of the fact that I've uninstalled any version or variant of Firefox, sometimes Hotmail works for me (rarely) but most times it doesn't.
It has to be some kind of plug-in issue, but I haven't found a solution to the problem.

Regards

---

