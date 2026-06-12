---
title: "Any Solution to this Aweful New 11.x Look?"
date: 2011-04-30
forum: General Help
---

### Post by matey3 on 2011-04-30
This is worse than frustrating. I dont know why these people always fix something which is NOT broken?
I just installed Ubuntu 11 and I wished I hadn't. Lot of the functionalities have been changed or are missing and programs shuffled where I cant even find the terminal.(so I had to ctrl alt F1 to get in and change /set password).
And the little up/down bar is terrible, you have to land your mouse on a hair thin line then quickly move ur pointer to the right to jump on this little up/down cursor button then move the mouse again to hit the up/down arrow (on this little capsule looking whatever)to move the page up and down and if you make a 1 millimeter mistake you have start the whole dumb routine again, this really sucks, now I have to use the cursor keys on the keyboard.
I tried different themes to no avail!?

anyone has any solution? Can I change the look to the older version or should I just ditch the whole thing. 
Thanks!

---

### Post by howefield on 2011-04-30
At the login screen, click on your user name, then Ubuntu Classic from the session menu on the bottom panel.

---

### Post by teachop on 2011-04-30
> **matey3 said:**
> This is worse than frustrating. I dont know why these people always fix something which is NOT broken?
I just installed Ubuntu 11 and I wished I hadn't. Lot of the functionalities have been changed or are missing and programs shuffled where I cant even find the terminal.(so I had to ctrl alt F1 to get in and change /set password).
And the little up/down bar is terrible, you have to land your mouse on a hair thin line then quickly move ur pointer to the right to jump on this little up/down cursor button then move the mouse again to hit the up/down arrow (on this little capsule looking whatever)to move the page up and down and if you make a 1 millimeter mistake you have start the whole dumb routine again, this really sucks, now I have to use the cursor keys on the keyboard.
I tried different themes to no avail!?

anyone has any solution? Can I change the look to the older version or should I just ditch the whole thing. 
Thanks!
Probably the quickest thing to try is to log out, and after you click your login name, select "Classic" at the bottom of the screen, then enter your password.  You will have a more familar interface and can always try Unity again any time.  It is also possible to disable the overlay scrollbars, I did, don't care for that either.

---

### Post by Lateralis on 2011-04-30
I hear you matey3.  You're not alone in disliking Unity.  As a temporary solution, you can make use of the classic Gnome look.  At the login screen, you can select which environment to use: Classic Gnome or Unity.  

Long term, Gnome 2 (Gnome in *buntu 10.x and before) is no longer supported - the Gnome project team are working on Gnome 3 and are discontinuing support for Gnome 2.  Gnome 3 and Gnome shell will be available to download through the main repos in Ubuntu 11.10, but they will not be installed by default.  If neither of these take your fancy, you can install other desktop environment next to Unity.  For instance KDE (kubuntu-desktop), LXDE (lubuntu-desktop) or Xfce (xubuntu-desktop).  You can again choose which one of these to use at start up.  If you like Gnome 2 then you might want to try out Xfce.

---

### Post by teachop on 2011-04-30
Here is the way to disable the overlay scrollbars:

Create a file /etc/X11/Xsession.d/80overlayscrollbars that contains the following:```
export LIBOVERLAY_SCROLLBAR=0
```

---

### Post by matey3 on 2011-04-30
A BIG Thank You to All of YOU for your kind replies. I somehow lost my wireless connection when tried to re log in?
I'll take a look at the logon screen again.I didnt really see that option? I'll look again.
Thanks a lot. I appreciate all your help!
Regards;

---

### Post by mdmcginn on 2011-04-30
The problem is that my login screen doesn't give me options to log in with a different mode or user. But you can change back to Ubuntu Classic using the Ubuntu System Settings. 
[http://ubuntuforums.org/showpost.php?p=10744544&postcount=10](http://ubuntuforums.org/showpost.php?p=10744544&postcount=10)

---

### Post by wordmaster on 2011-04-30
Thank you for telling me how to get to classic desktop. I read somewhere the new "look" was similar to Mac. Maybe that is why I was never interested in owning a Mac.

Everything is much easier to work with and to find in the classic. If the new one is going to be the future of Ubuntu, maybe it is time to look at some other distros or, heaven forbid, go back to windoze.

---

### Post by matey3 on 2011-04-30
BTW you can grab that up/down slide thing with your mouse and move the whole thing. I just figured it out but still too hard for me to deal with.
Some of the windows have the old style slider but some have the new kind (such as Ubuntu Software Center). Also FireFox 4.0 is little different too? It looks too much like Chrome (google), I like to say that having less tools, menus etc, is not necessarily better. (sort of Like when the 1st Windoze XP were shipped, they looked like a bad crayon job)!

I am sorry but I am an old dog (but with a choice) and dont like new tricks lol.

(Wordmaster): I also thought that the new version of Ubuntu looks like Mac. (shouldn't it be the other way around tho)?

Anyways thanks for all the replies and solutions. I am going to keep this install now!
:)

---

### Post by Lateralis on 2011-04-30
Both IE and Opera have gone down the Chrome route.  Personally, I quite like the additional real estate but I do want menus to be logical and clear.  There's nothing worse than having to dig around for options which were simple before.  On that front, Firefox 4 in Ubuntu and Opera are actually the best I've used.  I'm also moving away from Chrome (privacy issues, memory/resources usage issues and ease-of-use issues).  

As for a bad crayon job, that's exactly what I feel about Office 2007 and later with the whole "ribbon" menu shizzle.  Utter pants!

---

### Post by MountainX on 2011-05-01
> **howefield said:**
> At the login screen, click on your user name, then Ubuntu Classic from the session menu on the bottom panel.

This is a real problem when the user account is set to log in automatically without entering the password. Is there another way to log in with Classic mode?

EDIT: here's the solution: [http://ubuntuforums.org/showpost.php?p=10744544&postcount=10](http://ubuntuforums.org/showpost.php?p=10744544&postcount=10)

---

### Post by Jesus_Valdez on 2011-05-01
> **MountainX said:**
> This is a real problem when the user account is set to log in automatically without entering the password. Is there another way to log in with Classic mode?

EDIT: here's the solution: [http://ubuntuforums.org/showpost.php?p=10744544&postcount=10](http://ubuntuforums.org/showpost.php?p=10744544&postcount=10)
you can log out and do the change, I don't see the difficulty.

---

### Post by Lateralis on 2011-05-01
You only get the session menu if you have to enter a password to gain access to your account.  If you are logged in automagically you do not get the session selector, so you cannot make the choice between Unity and classic Gnome at login.  In this situation you have to change the system default as described in the above link.

---

