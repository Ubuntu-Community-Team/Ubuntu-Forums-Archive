---
title: "full screen webpage password protected"
date: 2011-05-31
forum: General Help
---

### Post by hplh on 2011-05-31
Hello guys!

This is my first post here so I hope I am not doing anything wrong.

I really need to display a full screen webpage with firefox (with flash animations, etc) with some password protection against navigating away, closing firefox, etc.

I am thinking that a good solution would be to set up gnome screensaver to display the webpage as it already has the password protection stuff. Anyway, I investigated this idea for a while and is seems that it will not work...

As I want to have flash animations onto that page, a solution that captures the screen and passes the picture to gnome is also not suitable.

So, please, if you have any other suggestions, let me know, as I have ran out of ideas.

Thanks,
Paul H.

---

### Post by searchfgold6789 on 2011-05-31
I would try first displaying the webpage as normal, then unplugging the mouse and keyboard. :p Then NO ONE will have the proper permissions.

---

### Post by hplh on 2011-05-31
I cannot find any cables to unplug for a laptop keyboard :)

---

### Post by hplh on 2011-05-31
I think a transparent screen saver can also do the trick, but I cannot find one. 

Can anyone help?

---

### Post by Trastle on 2011-06-25
I know this is a little late but the application you are looking for is "xtrlock".

Install it by running:
[FONT="Courier New"]sudo apt-get install xtrlock[/FONT]

Then launch xtrlock by running:
[FONT="Courier New"]xtrlock[/FONT]

This will start xtrlock lock your inputs (keyboard, mouse etc).
To unlock your desktop type your password and hit enter.

I was trying to work this out recently too and posted a couple of solutions [here]("http://blog.troyastle.com/2011/04/lock-input-without-screen-saver-in.html"). The above solution was the best I found.

---

### Post by Abir Valg on 2011-06-25
Another solution would be to use
[http://startpage.com]("http://startpage.com") and lookup firefox kiosk mode

---

### Post by enimeizoo on 2011-06-25
> **hplh said:**
> I cannot find any cables to unplug for a laptop keyboard :)

You can still unmap evrey single key... :twisted:

---

### Post by Jose Catre-Vandis on 2011-06-25
> **Trastle said:**
> I know this is a little late but the application you are looking for is "xtrlock".

Install it by running:
[FONT="Courier New"]sudo apt-get install xtrlock[/FONT]

Then launch xtrlock by running:
[FONT="Courier New"]xtrlock[/FONT]

This will start xtrlock lock your inputs (keyboard, mouse etc).
To unlock your desktop type your password and hit enter.

I was trying to work this out recently too and posted a couple of solutions [here]("http://blog.troyastle.com/2011/04/lock-input-without-screen-saver-in.html"). The above solution was the best I found.

Thanks Trastle - useful to know and have - panicked first time though as password didn't unlock, remember to press Enter first (if any keystrokes have been made), then type password, then type Enter again ;)

---

