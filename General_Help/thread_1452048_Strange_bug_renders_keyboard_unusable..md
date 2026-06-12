---
title: "Strange bug renders keyboard unusable."
date: 2010-04-11
forum: General Help
---

### Post by Agapooka on 2010-04-11
Greetings!

I have encountered the strangest bug, filled with so many inconsistencies that I am unable to comprehend why or how it is happening. It has only happened once and whilst it seems to resemble another bug that I found when looking for this one, it is fundamentally different. Here are the facts:

1. I am using an Acer Aspire One netbook.
2. This netbook is running Ubuntu 9.10.
3. It has been running Ubuntu 9.10 since the first time it was released as stable.
4. Yesterday, whilst I was engaging in an intellectually stimulating debate through the convenience of Pidgin, I encountered the said bug with the following attributes:

[LIST]
[*]**The keyboard has the appearance of not working.**
[*]**But if one applies a lot of pressure to each key, one is able to type.**
[*]**This bug is not resolved by a system reset.**
[*]**This bug does not affect my BIOS or even Ubuntu until I log into the particular account where it first happened.**
[*]**When I log out of the account and log into another one, my keyboard is perfectly responsive.**
[*]**When I log back into the "damaged account", the keyboard is once more unusable.**
[*]**The right click menus do work, in stark contrast to another, similar bug, the report of which I encountered in my search for this one.**
[/LIST]
So, clearly, an undesirable workaround would be to migrate to a new user on my system. This, however, does not change the fact that I do not wish to do this another time if the bug repeats itself. Furthermore, if it is only active in a session of the "damaged account", it is likely that it is a configuration error of sorts, no? I have another strange configuration error on that account. The little icon that allows me to choose to which wireless network I wish to connect is random in when it chooses to appear or not, although the service is active (as I am greeted with a message directing me to click on the non-existing icon in order to select the network...). Yet again, this only happens when logged into a particular user, while other users seem completely unaffected.

What I conclude from this is that Ubuntu's configuration system is pretty erratic and it makes seemingly random yet seemingly irreversible changes to user configuration. I would not even know where to start when faced with reading through different configuration files. Furthermore, I would feel as though my PC were constantly working against me. It is a strange feeling, when I bought it with the intention that we might work together...


Whimsically yours,
Agapooka

---

### Post by Agapooka on 2010-04-17
Wow, I'm surprised that there is no community interest in this issue at all.

It's been almost a week and the problem persists, of course, seeing as I don't even understand exactly how or why the problem happened. It had the appearance of being random, although I doubt that it was and believe there was a cause, I do not know more than I've already said.

Anyway, I'd like to thank all the people who contributed to attempting to solve this problem.

Thanks me, and well, me again. I'm sorry that you weren't able to help, but at least you tried!

Agapooka

---

### Post by Marlonsm on 2010-04-17
I've never seen such a bug, all I can think of right now is to try with an external keyboard (borrow one and put in the USB port). This way you will know if it is hardware-related or not.

---

### Post by Agapooka on 2010-04-17
I know the problem is not hardware related. The keyboard works perfectly fine when I am logged into a different user account in Ubuntu, in Grub and in Windows.

Yet the keyboard is not completely disabled when I am logged into my original user account, it just requires that one push the keys really hard in order to respond.

Is there a setting that affects keyboard sensitivity? Either way, the only thing I can see is that the problem is related to user configuration, although I did not alter it. 

Thank-you for your reply, though. I really appreciate it, considering the fact that this topic garnered absolutely no interest for over 6 days.


Agapooka

---

### Post by Marlonsm on 2010-04-17
Well, I can't really understand what is happening, I don't think keyboard have pressure sensors under the keys, the computer only knows whether a key is pressed or not, but not how much pressure is over it.
Have you tried just holding the key pressed (with a normal pressure) for some time. If it does register the key like that, all you'll need to do is to change the settings for the keyboard in the preferences menu.

---

### Post by Agapooka on 2010-04-17
Which is why I was confused.

I've since tried your idea of pressing the keys for a long time with normal pressure and it did indeed work.

Seeing as this happened while I was simply using the keyboard normally, I didn't know where to start looking. Also, because I was looking for the wrong thing, I overlooked the "only accept long presses" option, which was checked, although I had never altered it.

While the situation remains a mystery to me in how it came about, I would like to formally extend my thanks to you for solving it.

Cheers,

Agapooka

---

### Post by Marlonsm on 2010-04-17
Glad it worked and sorry for taking so long for someone to find this thread, there is so many people using this forum that sometimes posts quickly get out of sight.

---

