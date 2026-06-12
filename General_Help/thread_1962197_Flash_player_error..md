---
title: "Flash player error."
date: 2012-04-20
forum: General Help
---

### Post by joemcummings on 2012-04-20
I have a problem that I believe exists with flash player, such that it will not allow speedtest to run. I do have the codecs?? installed.

Thanks,

Joe

---

### Post by wojox on 2012-04-20
Do you have another plugin that is blocking it? Can you see other flash content?

---

### Post by ajgreeny on 2012-04-20
What is the situation of other flash sites?

There has been an update of adobe flash recently to 11.2.202.228 which has caused a lot of problems, with flash either not working at all, or showing everything with a blue colour tint.

For full info see [http://ubuntuforums.org/showthread.php?t=1948626](http://ubuntuforums.org/showthread.php?t=1948626) with the possible solutions shown at post 80 of the thread, and several other posts on it as well.  I had to downgrade to the 11.1 version which has some security risks, but if there is no other answer, it may have to be your way as well.

---

### Post by joemcummings on 2012-04-20
Yes, I don't think anything is really working with the flash player. Thanks, I wonder what the solution is going to be?

---

### Post by ajgreeny on 2012-04-21
> **joemcummings said:**
> Yes, I don't think anything is really working with the flash player. Thanks, I wonder what the solution is going to be?
The solution is probably in the thread that I linked to in my last post.

Look at post No 80 in that thread and follow the link in that to [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796) which tells you how to download the previous flash version, which does work well.

---

### Post by joemcummings on 2012-04-22
Yes, I understand the idea of going back to a previous version. As you mentioned, there is the security risk with doing that. What I meant to ask is will they probably update the software to fix the problem, or do I have to try something like using a previous version. Is this one of the reasons people go ahead and move to the next stable version of Linux?

Thank you for your help,

Joe

---

### Post by ajgreeny on 2012-04-22
> **joemcummings said:**
> Yes, I understand the idea of going back to a previous version. As you mentioned, there is the security risk with doing that. What I meant to ask is will they probably update the software to fix the problem, or do I have to try something like using a previous version. Is this one of the reasons people go ahead and move to the next stable version of Linux?

Thank you for your help,

Joe
Adobe will not be doing anything to overcome this problem, as they are not supporting any further versions of flash on linux.

What we need is the pepperpot flash which google are adding to chrome (not sure about chromium) or for gnash to be developed much more than it is at the moment.  There is also the hope of  html5 overtaking all of this, but I wouldn't hold your breath waiting.

---

### Post by lovinglinux on 2012-04-24
> **ajgreeny said:**
> Adobe will not be doing anything to overcome this problem, as they are not supporting any further versions of flash on linux.

What we need is the pepperpot flash which google are adding to chrome (not sure about chromium) or for gnash to be developed much more than it is at the moment.  There is also the hope of  html5 overtaking all of this, but I wouldn't hold your breath waiting.

Chromium won't have PepperFlash, since flash is proprietary. That's why it doesn't ship with flash already, like Chrome does.

If you are on 64bit system, you can try Chrome unstable. It comes with PepperFlash already.

However, the latest flash version is working on Opera and Firefox when viewing speedtest.net. I have tested here, but I don't have nVidia.

Try [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/).

---

