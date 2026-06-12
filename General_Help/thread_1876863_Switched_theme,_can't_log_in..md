---
title: "Switched theme, can't log in."
date: 2011-11-07
forum: General Help
---

### Post by whalogreg on 2011-11-07
I used the GNOME-tweak-tool to switch to the 'Elements' theme, which I grabbed from gnome-look.org, in 11.10. As soon as I chose the theme it logged me out and now I cannot log back in under that user. Anybody have a clue?

---

### Post by raja.genupula on 2011-11-07
while doing the login from login screen you gonna have recovery option may be that gonna solve. are you getting any type error messages while doing login  i mean authentication error or anything else ?

---

### Post by whalogreg on 2011-11-07
I tried logging in under GNOME (shell), Ubutnu (untiy), Unity 2d, every option available. The same result with every attempt. I don't get any errors. I type in my password, hit enter, the screen flickers for a second and goes right back to the login screen. This is on a fresh install, not much done at all. 

Or were you talking about a recovery option from Grub?

---

### Post by cbowman57 on 2011-11-07
From the login screen hit ctl+alt+f1 to take you to a tty terminal.  Login then ...

move or rename the Elements folder, I'm fairly certain if the theme is missing it will default to Adwaita & let you log in.

---

### Post by whalogreg on 2011-11-07
So I tried deleting the folder containing the theme. The name of the folder is "Elements(Unity)". When I try deleting it, I get an error saying something along the lines of... unexpected character "("

so the command line errors out when it gets to the parentheses in the name of the folder I need to delete.

---

### Post by cbowman57 on 2011-11-07
You probably already tried this but did you try it with & without quotes?

You could also boot up with a liveCD and use nautilus from that to remove the directory.

---

### Post by whalogreg on 2011-11-07
> **cbowman57 said:**
> You probably already tried this but did you try it with & without quotes?

You could also boot up with a liveCD and use nautilus from that to remove the directory.

I did try it without the parentheses and it did not work... what DID work was "Elements*"... Defaulted back to Adwaita. Thanks for the help!

---

### Post by cbowman57 on 2011-11-07
Super.  I was pretty certain that would work, glad you had access from another machine to sort this out. :)

---

### Post by whalogreg on 2011-11-07
> **cbowman57 said:**
> Super.  I was pretty certain that would work, glad you had access from another machine to sort this out. :)

Well, same machine... different partition. ha

---

### Post by cbowman57 on 2011-11-07
> **whalogreg said:**
> Well, same machine... different partition. ha

Yeah, I considered that after I'd posted, or even just from the live session.  :)

---

