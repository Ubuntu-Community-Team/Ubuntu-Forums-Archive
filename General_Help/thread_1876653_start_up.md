---
title: "start up"
date: 2011-11-06
forum: General Help
---

### Post by goldshirt9 on 2011-11-06
I am using ubuntu 11.10
and at start up i get the grub screen option to choose which version option i wish to boot into.
as this is a fresh install i have only 1 option.
i wish to bypass this screen , no i want to by pass this screen.
how do i do this. :confused:

also where do i find the gnome tweak shell extension to remove the 
universal access setting in gnome 3 on the top panel.
i seem to have lost my link to it :(

---

### Post by mike555 on 2011-11-06
You will need to edit grub, and set time out to 0

---

### Post by goldshirt9 on 2011-11-07
thanks for the help
found this on another page as how to do it

> **drs305 said:**
> The default menu behavior for Grub 2 is to not  display the menu on single OS machines (which is probably one reason *Rubi1200*  asked). To display the menu, if you want to see it on every boot, you  place a comment in front of the GRUB_HIDDEN_TIMEOUT line in  /etc/default/grub:


Even though you don't want to see the menu, since it's inconsistent for  you now perhaps you should try commenting the above. Then set the  timeout for 1 second to see if it consistently boots without manual  intervention.

I don't know all the events that trigger a recordfail event. It can be  triggered if a boot is interrupted/aborted. The next time Ubuntu starts  it remembers the previous failure and displays the menu so the user can  elect a different option if desired.

I believe, though I haven't tested it since Grub 1.96, that the  recordfail event is noted in /boot/grub/grubenv. If that is the case,  you can try to clear it with "sudo grub-editenv create", although for a  one-time interrupted boot it should clear automatically after the next  successful boot.

can someone advise as to how i mark this as solved ???

---

### Post by Matti L on 2011-11-07
Click on the "Thread Tools" above your first post and click "Mark this thread as solved".

---

### Post by goldshirt9 on 2011-11-07
cheers
and i found answer to the second question  @
[http://www.webupd8.org/2011/05/more-gnome-shell-extensions-mediaplayer.htm](http://www.webupd8.org/2011/05/more-gnome-shell-extensions-mediaplayer.htm)

---

