---
title: "Chrome/Chromium Crashes on Sign-In"
date: 2011-12-20
forum: General Help
---

### Post by rjf1 on 2011-12-20
Just installed 11.10 a few days ago. Was able to use Chromium -- no problem. The next day, I updated a couple hundred files (automatic update manager picked files). After the update, Chromium would crash when I tried to sign into my gmail page. Didn't affect the rest of the system -- it just shut down and disappeared from the desktop.

Just to check, I downloaded and installed Chrome from the google site -- ran it -- crashed exactly the same. I can run both Chromium and Chrome just fine on any pages that don't require a Google sign in -- as soon as either of them hit any of the google pages they turn out like a light.

Anyone else seen this -- know anything about it? Obviously, Chrome/Chromium isn't getting along with something in the upgrade -- but what? and how to fix?

---

### Post by BC59 on 2011-12-20
Open your /home directory and press CTRL+H to see the hidden folders. Then go to /.config and delete the google-chrome folder. I'm not sure if there is a folder for google-chromium to delete it as well.
Then try to open Chrome and Chromium.

---

### Post by BC59 on 2011-12-20
I forgot to tell you, that you are going to lose this way your bookmarks and extensions installed. If you have a problem with them don't delete from the trash the old chrome folders. I will tell you how you can recover the bookmarks.

---

### Post by rjf1 on 2011-12-20
> **BC59 said:**
> Open your /home directory and press CTRL+H to see the hidden folders. Then go to /.config and delete the google-chrome folder. I'm not sure if there is a folder for google-chromium to delete it as well.
Then try to open Chrome and Chromium.

Thanks for your reply. I had already tried that -- but they get recreated each time and as soon as I try to sign in, the whole thing starts all over.

---

### Post by BC59 on 2011-12-20
Are you sure you don't have any graphic card issue? Did you install the proprietary drivers?

---

### Post by rjf1 on 2011-12-22
I installed the proprietary drivers right away after installing Ubuntu -- there was no problem with the crashing. It only started after the huge upgrade that happened afterwards.

As an experiment, I installed Ubuntu on another machine, and when the upgrade manager came up with the huge upgrade, I deselected all the kernel upgrade files. After that upgrade Chromium worked as expected without crashing. So, I'm guessing that something in the new kernel is causing a conflict -- I haven't tried upgrading the kernel files on the second machine -- I'm afraid I'll see the crashing problem.

---

### Post by beerguzzler on 2011-12-22
I have pretty much the same issue so you're not alone.
Works fine if you go on a normal page like a news site, but as soon as you try to access FB/Twitter/gmail etc it crashes with a Kill pages pop up. Even if you do that you still have to delete the files suggested in the earlier post to get the browser to work again. 

Take a look on Google's forums and you see plenty of users with the same issue. IMO, the browser simply isn't ready for Linux.

---

### Post by rjf1 on 2011-12-22
> **beerguzzler said:**
> Take a look on Google's forums and you see plenty of users with the same issue. IMO, the browser simply isn't ready for Linux.
There was no problem with it prior to the kernel upgrade, and I have no problem with it on my 2010.2 Mandriva system -- so I don't think it's a case of the browser not being ready for Linux. My guess is that the new kernel threw it a curve. Just have to wait until they get it sorted out.

---

### Post by BC59 on 2011-12-22
If you think it's the kernel, go [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") and install one of the list.
In case of a problem, boot and choose your previous one from the Grub menu.

---

### Post by beerguzzler on 2011-12-22
Adding the [Chromium daily build repo ]("https://launchpad.net/~chromium-daily/+archive/ppa")may help too. I've just done so and updated and it actually seems to have cured the issues I had.

---

### Post by rjf1 on 2011-12-22
> **beerguzzler said:**
> Adding the [Chromium daily build repo ]("https://launchpad.net/~chromium-daily/+archive/ppa")may help too. I've just done so and updated and it actually seems to have cured the issues I had.

That worked for me, too. Thanks.

---

