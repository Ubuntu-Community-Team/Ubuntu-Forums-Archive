---
title: "Cannot enter the desktop and pass the Login screen"
date: 2011-03-22
forum: General Help
---

### Post by tribald on 2011-03-22
Hi all, my ubuntu 10.10 64bit (in Dell Latitude machine) login screen is not working. the blank bar to type username and password is not appearing at all. In a quick appeareance there also a sentence: "permission denied". I've tried to browse this forum and seems no answer. I still can access the terminal though using alt+ctrl+F2 but i don't know how to access the desktop because when i hit alt+F7 it come back to login screen. how can i fix it? I have several files in the laptop that need to be saved, if not I probably just clean install it. Please anyone help me. Thanks

---

### Post by bluefrog on 2011-03-22
certainly just a matter of wrong permissions on some of your home files/folders.

log on via the terminal, create yourself another user (sudo adduser)
add the user to the admin group (sudo gpasswd -a new-user admin)

go to the login screen (F7). log on with your new user and see what happens

---

### Post by tribald on 2011-03-22
> **bluefrog said:**
> certainly just a matter of wrong permissions on some of your home files/folders.

log on via the terminal, create yourself another user (sudo adduser)
add the user to the admin group (sudo gpasswd -a new-user admin)

go to the login screen (F7). log on with your new user and see what happens

Hi, thanks for your reply. I already type "sudo adduser" and the machine replies 

"adduser: Only one or two names allowed."

seems i can't add another user.

---

### Post by vivek.pandey on 2011-03-22
> **tribald said:**
> Hi all, my ubuntu 10.10 64bit (in Dell Latitude machine) login screen is not working. the blank bar to type username and password is not appearing at all. In a quick appeareance there also a sentence: "permission denied". I've tried to browse this forum and seems no answer. I still can access the terminal though using alt+ctrl+F2 but i don't know how to access the desktop because when i hit alt+F7 it come back to login screen. how can i fix it? l
when you get the terminal using ctrl+alt+f2 are you there in some account ?
anyways you can start x server to get a gui 
```
 startx 
```

---

### Post by tribald on 2011-03-22
> **vivek.pandey said:**
> when you get the terminal using ctrl+alt+f2 are you there in some account ?
anyways you can start x server to get a gui 
```
 startx 
```

I can't open any account except hit "alt+ctrl+F2" first and log in from terminal. I've tried the startx but the result is:

"Fatal Server Error:
cannot establish any listening socket - make sure x server isn't already running."

---

### Post by vivek.pandey on 2011-03-22
ok may be your x server is already running.. ok can you please explain the entire scenario from the time you switch on the machine

---

### Post by tribald on 2011-03-23
> **vivek.pandey said:**
> ok may be your x server is already running.. ok can you please explain the entire scenario from the time you switch on the machine

After I switch on the machine the grub is loading Ubuntu and the boot screen is on. Then a box came up:

"There is a problem with the configuration server.
(/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)"
with a button named: X Close

the box above just appear recently.

when i hit the button X Close the screen enter the login screen with username and picture. When i hit the name nothing happen where it should pop up a blank box to enter the password. Instead a sentence "permision denied" is quickly appear and gone.

At the bottom right screen there is a box written: 


"Install problem!
The configuration defaults for GNOME Power Manager have not been installed correctly."

What should i do? should I reinstall everything? If i have to reinstall how to do it because i don't have any maverick CD. I did the upgrade through internet. I post this message through other computer.

---

### Post by tribald on 2011-03-24
I think i will reinstall the Ubuntu then. Is there any way to have the data i need not deleted? or the only way is just using live CD and back it up all?

---

### Post by hakermania on 2011-03-24
Hmmm...An idea came to my mind, did you unistall nautilus???

---

### Post by jerome1232 on 2011-03-24
It's really hard to figure out what wrong, what were your doing before this happened? Upgrade some packages? Did you do that distribution upgrade and then this happened?

Were you changeing some configuration's? changing permissions on something? Installing something?

Anything you can think of that you have changed recently before this started happening.

---

### Post by tribald on 2011-03-25
> **hakermania said:**
> Hmmm...An idea came to my mind, did you unistall nautilus???

I don't know if i uninstalled it.

> **jerome1232 said:**
> It's really hard to figure out what wrong, what were your doing before this happened? Upgrade some packages? Did you do that distribution upgrade and then this happened?

Were you changeing some configuration's? changing permissions on something? Installing something?

Anything you can think of that you have changed recently before this started happening.

It happen after I put login screen back on. couple of weeks ago i turn off the login screen, then couple of days after (i forget the exact day) the keyring asking for password start to bother me because it always happen. And somehow it happen three times in a row. I assume that it is because of the login screen so i put it back on, and that is when the case happening. 

But don't be bothered anymore, I already did a clean install now. I save the data by using the live CD, it consumed a lot of time but i managed to save and have Maverick back on again. 


Thank you very much for your kind response.

---

