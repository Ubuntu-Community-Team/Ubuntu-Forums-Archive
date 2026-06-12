---
title: "Firefof logs residing in home document folder!!!!"
date: 2010-04-26
forum: General Help
---

### Post by emma00 on 2010-04-26
Hi,

Today i was looking for my assignment and i found it in documents folder.I also found some strange icon looking files and folders too such as urlclassified3.sqlite and many more i did not know what it was and i deleted it but somehow i know it was related to firefox, because there was a test pilot error log and i deleted it too and next when i opened firefox my bookmarks and personas were gone i don't know what happened and there are now new files and folders which have made  it self in documents folder again  anybody know what to do with it????:confused:

---

### Post by cariboo on 2010-04-26
Press Alt-F2 and type:

```
firefox -Profilemanager
```

to see if you are using the correct profile. If you haven't changed anything it should be the default profile.

---

### Post by lovinglinux on 2010-04-27
Looks like you have changed the location of your Firefox profile to your home folder, so Firefox is saving its files (bookmarks, databases, settings...) in your documents folder.

Do what cariboo907 suggested, delete the current profile (you will loose all Firefox settings), then create a new one without modifying the default location. You Firefox files will be placed under ~/.mozilla/firefox/<profilename>

---

### Post by emma00 on 2010-04-27
> **cariboo907 said:**
> Press Alt-F2 and type:

```
firefox -Profilemanager
```to see if you are using the correct profile. If you haven't changed anything it should be the default profile.

I runed it and  a new firefox window came up nothing else and the settings are same which i am using as default and thanks too.

> **lovinglinux said:**
> Looks like you have changed the location of your Firefox profile to your home folder, so Firefox is saving its files (bookmarks, databases, settings...) in your documents folder.

Do what cariboo907 suggested, delete the current profile (you will loose all Firefox settings), then create a new one without modifying the default location. You Firefox files will be placed under ~/.mozilla/firefox/<profilename>

How i delete this profile??? and create new one and thanks

---

### Post by lovinglinux on 2010-04-27
> **emma00 said:**
> I runed it and  a new firefox window came up nothing else and the settings are same which i am using as default and thanks too.



How i delete this profile??? and create new one and thanks

Close Firefox, then run this on the terminal:

```
firefox -P
```

Then select the profile and click the delete button, choose the option to delete the files too when prompted, then click the "Create Profile" button to create a new one (don't change the default profile location):

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=154500&stc=1&d=1272410472[/IMG]

---

### Post by emma00 on 2010-04-30
> **lovinglinux said:**
> Close Firefox, then run this on the terminal:

```
firefox -P
```Then select the profile and click the delete button, choose the option to delete the files too when prompted, then click the "Create Profile" button to create a new one (don't change the default profile location):

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=154500&stc=1&d=1272410472[/IMG]

Thanks it really worked by da way why you have done this on your blog????

---

### Post by lovinglinux on 2010-04-30
> **emma00 said:**
> Thanks it really worked by da way why you have done this on your blog????

Because I only get spam. I might open the comments again, but I need to setup a spam filter first.

---

### Post by emma00 on 2010-05-01
> **lovinglinux said:**
> Because I only get spam. I might open the comments again, but I need to setup a spam filter first.

When will you open it then i will comment have to ask something:lolflag:
Thanks a lot.

---

### Post by lovinglinux on 2010-05-01
> **emma00 said:**
> When will you open it then i will comment have to ask something:lolflag:
Thanks a lot.

Then use the [Support Ticket](http://lovinglinux.megabyet.net/?page_id=728) system. If it is about Firefox issues, you can post in the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

EDIT: is open again, after all the spam keeps coming on other sections :)

---

### Post by emma00 on 2010-05-02
> **lovinglinux said:**
> then use the [support ticket]("http://lovinglinux.megabyet.net/?page_id=728") system. If it is about firefox issues, you can post in the [firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567").

Edit: Is open again, after all the spam keeps coming on other sections :)

ok posted.

---

### Post by lovinglinux on 2010-05-02
> **emma00 said:**
> ok posted.

replied :)

---

### Post by emma00 on 2010-05-03
> **lovinglinux said:**
> replied :)

one more...:P

you upgraded ubuntu to 10.04 or did a clean install????:popcorn:

---

### Post by lovinglinux on 2010-05-03
> **emma00 said:**
> one more...:P

you upgraded ubuntu to 10.04 or did a clean install????:popcorn:

I always do clean installs.

---

### Post by emma00 on 2010-05-04
> **lovinglinux said:**
> I always do clean installs.

why????

Is there any problem with upgrade????:o

and i encountered a new problem with firefox i was actually attaching a file of 10 MB and while it was being attached the page becomes black and i minimized it and than it becomes irrresponsive and  all of the  other pages were also showing the same thing when i force quit it and restarted firefox it was ok but whenever i tried to mai0,l it did the same thing and than i used chrome nothing happened there.:confused:

---

### Post by lovinglinux on 2010-05-04
> **emma00 said:**
> why????

Is there any problem with upgrade????:o

Well, I just don't trust it :) In fact, I never did an upgrade in my Ubuntu life, but after each new release I see several threads from people experiencing problems that have upgraded instead of installing from fresh. Anyway, doing clean installs is very fast. I have a separate partition, so I can keep my settings. I also use my [Umarks](http://lovinglinux.megabyet.net/?page_id=534) extension to re-install non-default applications and I have a checklist of everything I need to configure outside home, so I can have my system back in no time. Besides, I always install a command-line system from the alternate CD and install kde-minimal. I'm not sure how an upgrade will behave in this scenario. Perhaps I should try it on a VM, just o see what happens, but I will continue doing clean installs anyway :)

Clean installs also have the advantage of removing any possible malware. I never had such problems, but it is comforting to know your system is pristine.

> **emma00 said:**
> and i encountered a new problem with firefox i was actually attaching a file of 10 MB and while it was being attached the page becomes black and i minimized it and than it becomes irrresponsive and  all of the  other pages were also showing the same thing when i force quit it and restarted firefox it was ok but whenever i tried to mai0,l it did the same thing and than i used chrome nothing happened there.:confused:

What mail service you were using?

Try [Simple Mail](https://addons.mozilla.org/en-US/firefox/addon/5593) extension for Firefox.

---

### Post by emma00 on 2010-05-05
> **lovinglinux said:**
> Well, I just don't trust it :) In fact, I never did an upgrade in my Ubuntu life, but after each new release I see several threads from people experiencing problems that have upgraded instead of installing from fresh. Anyway, doing clean installs is very fast. I have a separate partition, so I can keep my settings. I also use my [Umarks]("http://lovinglinux.megabyet.net/?page_id=534") extension to re-install non-default applications and I have a checklist of everything I need to configure outside home, so I can have my system back in no time. Besides, I always install a command-line system from the alternate CD and install kde-minimal. I'm not sure how an upgrade will behave in this scenario. Perhaps I should try it on a VM, just o see what happens, but I will continue doing clean installs anyway :)

Clean installs also have the advantage of removing any possible malware. I never had such problems, but it is comforting to know your system is pristine.



What mail service you were using?

Try [Simple Mail]("https://addons.mozilla.org/en-US/firefox/addon/5593") extension for Firefox.


Then i think i should also do clean install but i have to wait for it because of my thesis.....

I was using my yahoo are you a firefox developer,you are always referring their extensions :lolflag: and how do you got to know so many things i also want to be good at it...........;)

---

### Post by lovinglinux on 2010-05-05
> **emma00 said:**
> ...are you a firefox developer,you are always referring their extensions :lolflag: and how do you got to know so many things i also want to be good at it...........;)

:lol:

No, I'm just an amateur [Firefox extension developer](https://addons.mozilla.org/en-US/firefox/user/4352153), but I use Firefox since version 0.9 I guess and I love extensions. I have [more than 50 installed](https://addons.mozilla.org/en-US/firefox/collection/lovinglinux) :)

---

### Post by emma00 on 2010-05-05
you called this amateur...............:lolflag:

A whole list of firefox extensions which i have saved now am still in a doubt you are in firefox...........:lolflag:

---

