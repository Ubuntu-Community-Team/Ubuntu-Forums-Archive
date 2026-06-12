---
title: "compiz no skydome"
date: 2011-11-02
forum: General Help
---

### Post by alex_foreman on 2011-11-02
Hi,
i have ubuntu 11.1 and have enabled the cube but i cant seem to set a skydome background image, all of the sites i have been on online have shown CompizConfig Setting manager to have a differant layout to mine, and there is no browse for image button next to the skydome image section, i have tried typing in the address of the image in the bar but this does not work.
Any help would be greatly appreciated!
Alex

---

### Post by stinkeye on 2011-11-02
Have you eabled the **jpeg** and/or **png** plugins under image loading

---

### Post by alex_foreman on 2011-11-07
yes i have now enabled these but now it has caused unity to dissapear and i cant open up terminal to reenable it, any help?

---

### Post by stinkeye on 2011-11-07
> **alex_foreman said:**
> yes i have now enabled these but now it has caused unity to dissapear and i cant open up terminal to reenable it, any help?

Try ctrl+alt+t
or

Log in to your 2d session and enable unity in ccsm from there.

---

### Post by alex_foreman on 2011-11-07
i have tried ctr alt t that dosnt work,
how do i open up 2d ubuntu (sorry nooby question)

cheers

---

### Post by stinkeye on 2011-11-07
> **alex_foreman said:**
> i have tried ctr alt t that dosnt work,
how do i open up 2d ubuntu (sorry nooby question)

cheers
At the login screen select your account then click on the gear wheel 
and choose ubuntu 2d.

---

### Post by alex_foreman on 2011-11-07
right i now have unity back and everything but whenever i click to enable png or jpeg it causes everything to be disabled again, and even when i have everything enabled, still no skydome

---

### Post by stinkeye on 2011-11-07
So, can you browse for a picture in skydome?

---

### Post by alex_foreman on 2011-11-08
no, my compiz looks like this

---

### Post by stinkeye on 2011-11-08
Did you upgrade from 11.04 or fresh install ?
You seem to be missing 3 tabs.
What version of ccsm are you using?
```
ccsm --version
```

eg```
glen@Oneiric:~$ ccsm --version
CCSM 0.9.5.92

```

---

### Post by alex_foreman on 2011-11-08
CCSM 0.9.5.92

and i upgraded from 10.04

---

### Post by stinkeye on 2011-11-08
You may have conflicting configs from your 11.04 install.

These commands will remove all your compiz configs.
You may want to do this from within the 2d session then log back into the ubuntu session.


Run the commands one at a time.
```
rm -rf .gconf/apps/compiz*
rm -rf .cache/compizconfig-1/
rm -rf .config/compiz-1/
rm -rf .compiz*
```



If ccsm still goesn't show properly, try creating a new account
system settings > user accounts
and see if ccsm displays the extra tabs in the Cube plugin when logged into that account.

---

### Post by alex_foreman on 2011-11-08
thank you very much!
you have fixed it :)

cheers again

Alex

---

