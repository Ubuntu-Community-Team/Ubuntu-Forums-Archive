---
title: "Firefox not showing links of a perticular website"
date: 2010-05-24
forum: General Help
---

### Post by Ouia on 2010-05-24
Hi,

I have this weird problem, and I have no idea where to start.

Since I'm using Ubuntu and it first occurred after I had problems with X or and Compiz, I'll try here first.

The problem actually lies with Firefox (3.0.19)

After I solved my problems, everything looked fine at first.
That was until I went to one particular website and found that some links were missing. They simply were not showing in the browser.
They were showing in the source code, so they should have appeared.

Now, I have two different profiles by using: ```
/usr/bin/firefox -p -no-remote
```
My other profile had no problems at all. So the source code should not be the problem.

But when I looked closer at the source code I noticed that the links that were missing were written in upper case 'HREF'.
Not every link on the website is missing and they were indeed written in lower case 'href'.

When I think of it now, the problem occurs with link that do not seem to have a permanent base. (forum-posts , email, specific pop-up that has an other URL every time.)

I am not yet aware that the problem occurs on other websites.

I have no idea where to start thinking about a solution. I assume it's either the website, Firefox,  add-on, or a plug-in.

I could reinstall the packages with the synaptic package manager, but I'm afraid I'll loose all my setting, themes, add-ons, plug-ins etc).
Another possibility is to make another profile and see if I can reproduce my old one. But that is a lot of effort for such a small problem. However, I use it alot so it is very annoying.

But I was really hoping someone knows an easier solution.:)

---

### Post by Irony on 2010-05-24
Close firefox, go to;

```
~/.mozilla
```

rename it;

```
~/.mozilla1
```

start firefox and see if the problem is solved.

---

### Post by Ouia on 2010-05-24
This is what I get.

geert@geert-desktop:~$ ~/.mozilla
bash: /home/geert/.mozilla: is a directory

---

### Post by Irony on 2010-05-24
I meant open up nautilus and navigate to your home directory press ctrl+H to reveal hidden directories, right click on .mozilla and rename it .mozilla1.

Then start up firefox, it will start up without any of your setting and so create a default .mozilla (you can restore your previous settings by then deleting this newly created .mozilla and renaming .mozilla1 to .mozilla).

Or... in terminal do;

```
mv ~/.mozilla ~/.mozilla1
```

---

### Post by Ouia on 2010-05-24
Thanks.

I tried it, but it did not work:(

---

### Post by lovinglinux on 2010-05-24
> **Irony said:**
> I meant open up nautilus and navigate to your home directory press ctrl+H to reveal hidden directories, right click on .mozilla and rename it .mozilla1.

Then start up firefox, it will start up without any of your setting and so create a default .mozilla (you can restore your previous settings by then deleting this newly created .mozilla and renaming .mozilla1 to .mozilla).

Or... in terminal do;

```
mv ~/.mozilla ~/.mozilla1
```

The OP said he/she doesn't want to lose settings, extensions and passwords. He/she also already created a new profile, which essentially the same as doing what you are suggesting, without removing the old profile.

@Ouia

Start Firefox in safe mode:

```
firefox -safe-mode
```

If you don't experience the same problem in safe mode, then is probably an extension messing with the links. See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567) for additional info on how to pinpoint the culprit.

---

### Post by Ouia on 2010-05-24
I had the right bookmarks and the links were back, so I'll have a look at that section..

Thanks :)

---

### Post by Ouia on 2010-05-25
The problem is fixed. Turns out it was adblock plus.

Re-installing adblock didn't do it, but after I updated the list the problem was gone.

Thanks.

---

### Post by Irony on 2010-05-25
> **lovinglinux said:**
> The OP said he/she doesn't want to lose settings, extensions and passwords.
Yes, well done - the purpose of my suggestion was in order to determine whether the problem was due to personal settings and extensions.

The OP has confirmed that it was adblock plus so on using my method he will see that it was something to do with personal settings and extensions - he could then have restored his settings and systematically eliminated and restored each extension to determine which it was.

---

### Post by lovinglinux on 2010-05-25
> **Irony said:**
> Yes, well done - the purpose of my suggestion was in order to determine whether the problem was due to personal settings and extensions.

The OP has confirmed that it was adblock plus so on using my method he will see that it was something to do with personal settings and extensions - he could then have restored his settings and systematically eliminated and restored each extension to determine which it was.

Yes, I know. The thing is that a lot of users recommend other users with Firefox problems to just delete or rename ~/.mozilla in order to fix any problem, without explaining how to get all the settings back or how to pinpoint the culprit. Although is an easy solution, is not necessarily the best solution for the user. I think is way much better to tell the user to create a new profile from profile manager. This will allow the user to determine if the problem is within it's profile, without forcing him to restore the settings if it doesn't work as expected. Besides, to determine if the problem is an extension, the user don't need to create a new profile or delete the one in use. He just needs to start Firefox in safe mode.

Is just my opinion anyway, but it bothers my how disseminated is the concept of deleting/renaming the .mozilla folder instead of explaining how to create a new testing profile.

---

