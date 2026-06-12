---
title: "Password in Konsole"
date: 2010-01-15
forum: General Help
---

### Post by Rental on 2010-01-15
hiya, recently stated using ubuntu, and installed Konsole. when i type try to become the superuser, i cant type my password in, flashes a little though. and when i do type my password in, it says its wrong. tried to look for a solution, but im out of ideas now =/

cheers

---

### Post by Portmanteaufu on 2010-01-15
> **Rental said:**
> hiya, recently stated using ubuntu, and installed Konsole. when i type try to become the superuser, i cant type my password in, flashes a little though. and when i do type my password in, it says its wrong. tried to look for a solution, but im out of ideas now =/

cheers

Welcome to the Ubuntu forums! This is actually a feature that catches a lot of newbies off-guard, but it's intentional.

The shell doesn't show you any of the characters you're typing as you type them in as a precaution. If they showed, say, an asterisk (*) for every character you entered, then someone watching over your shoulder might be able to count how many characters were in your password. It might seem a bit paranoid, but it's been like this since the dawn of time. If you dislike it, I think it's going to become an option rather than a standard in future versions of Ubuntu. (Advanced users can find more about this by reading the bug reports in the Hundred Paper Cuts project).

So! To sum up, just type in your password with confidence and hit enter. If it reports it as wrong, try a couple more times. If it's still saying it's wrong, give us a shout and we'll see if we can help.

---

### Post by Rental on 2010-01-15
thanks!
i had thought of that option, and like it, as with so many other little things i have discovered about ubuntu!, but i do still have the problem of the password being wrong, have been trying most of the day with no luck. i did change my password from the one i used in Wubi, both passwords dont work. any help would be appreciated! thanks

---

### Post by Kevbert on 2010-01-15
Welcome.
Don't forget that in Ubuntu/Linux the password is case sensitive, so 'Password' is different from 'password'.  Do you get the same problem with Terminal (Applications-Accessories-Terminal) ? as Konsole is the Kubuntu equivalent.

---

### Post by Rental on 2010-01-15
> **Kevbert said:**
> Welcome.
Don't forget that in Ubuntu/Linux the password is case sensitive, so 'Password' is different from 'password'.  Do you get the same problem with Terminal (Applications-Accessories-Terminal) ? as Konsole is the Kubuntu equivalent.

yeh i know that, tried. andd yep i did, i tried a different program because of the problem.

---

### Post by Portmanteaufu on 2010-01-15
You're sure you're typing the same password that you typed to log into Ubuntu in the first place? It seems odd that it would accept the password during the login but not in the terminal.

Try this: open a text file and type your password in it so you can see all the characters. This will let you see if, say, your "s" key has broken or if your keyboard is magically stuck in caps lock. Seeing that your password is showing up correctly will rule out a lot of silly little things.

Let us know if you detect weirdness.

---

### Post by nexoncore on 2010-01-15
You are an admin account arnt you, and not on a shared computer were you may be a desktop user.

As far as I recall, only Administrators can actually use upper level functions in terminal, such as sudo or anything requiring a password.

---

### Post by Rental on 2010-01-15
> **Portmanteaufu said:**
> You're sure you're typing the same password that you typed to log into Ubuntu in the first place? It seems odd that it would accept the password during the login but not in the terminal.

Try this: open a text file and type your password in it so you can see all the characters. This will let you see if, say, your "s" key has broken or if your keyboard is magically stuck in caps lock. Seeing that your password is showing up correctly will rule out a lot of silly little things.

Let us know if you detect weirdness.

nope, everythings fine. the password i put in is correct. i dont think im doing anything wrong, i may be new too ubuntu, but iv been around windows for years, so pritty pc knowledgeable. but i cant work this out! i dont see a problem =/ apart from the obvious

/nexoncore - yes i am :)

---

### Post by Kevbert on 2010-01-16
Just wondering if Konsole has been corrupted.
Please go to Applications-Accessories-Terminal and enter
```
sudo apt-get install -f
```
this will check for damaged packages.

---

### Post by Rental on 2010-01-16
> **Kevbert said:**
> Just wondering if Konsole has been corrupted.
Please go to Applications-Accessories-Terminal and enter
```
sudo apt-get install -f
```
this will check for damaged packages.
 nothing appears to be wrong. ahh this is quite irritating now =/. my password is wrong every time, although its what my password is. tried well over 100+ times now, and i dont understand whats wrong!
 
any help wiht this would be amasing, and thankyou too anyone who has tried to help.

---

### Post by Rental on 2010-01-16
fixed!

probably a very silly mistake, but in System > Administration > Users and Groups, i found that i had a password set for my user, but not the root user. i set a password, and volla!

thanks too anyone that that tried to help. Much Appreciated :)

---

