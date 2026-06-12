---
title: "This directory has been unmounted to protect your data"
date: 2011-02-14
forum: General Help
---

### Post by jchase45 on 2011-02-14
I had issues on my last install , I couldn't boot into it cause I accidentally uninstalled python 2.6 and everything it was attached to. So I reinstalled on a separate hard drive, I can see my other file system from the media folder but the only thing in my home dir is these 2 files 1 read me that says 

[PHP]

THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private
[/PHP]

and then this file 

Access-Your-Private-Data.desktop

but when I click it and try to run it I get this error 

[PHP]

Untrusted application launcher
The application launcher "Access-Your-Private-Data.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe.


[/PHP]

any ideas ??

---

### Post by jchase45 on 2011-02-15
No one?

---

### Post by tredegar on 2011-02-15
I am _guessing_ that you encrypted your home dir.

I have no experience of this, but what happens if you try the second sugggested solution, and run **ecryptfs-mount-private** in a terminal?

It'll either work, or show errors.

---

### Post by jchase45 on 2011-02-15
Nope. No errors , nothing happens at all. weird. Yea I encrypted my home drive 

[PHP]
jared@jared-EP45-DS3L:~$ ecryptfs-mount-private
jared@jared-EP45-DS3L:~$ 


[/PHP]

---

### Post by tredegar on 2011-02-15
Sorry that did not work for you, although if the command did not return any errors, according to 'nix / linux standards "it worked!"

Did you check that your data wasn't there, after that command? (Though I would have expected it to ask you for some sort of key).

You could try launching a root instance of nautilus with **gksudo nautilus** and then clicking **Access-Your-Private-Data.desktop** but I am just guessing here (and nobody else helped you).

If that fails, I'd suggest waiting a while and then posting a new thread with a better title, perhaps "Cannot access old (encrypted) /home partition. I have the encryption-key".

Somebody else must have been in the same situation.

Good luck.

---

### Post by jchase45 on 2011-02-15
Still get the untrusted application launcher error , but I did change the thread title lol

---

### Post by curtissthompson on 2011-03-08
Run Nautilus as root:

sudo Nautilus

Then navigate to your install's /home directory, right click the Access-Your-Private-Data.desktop file, click Properties and navigate to the Permissions tab. Execute: "Allow executing file as program" will be unchecked, make sure you put a check mark for it, then click Close.

I've gotten that much to work for me, but am experiencing trouble myself getting past this point, as when I double click "Access-Your-Private-Data.desktop" the terminal opens for a split second and closes with no change in my ability to access the encrypted directory.  I've read the terminal should open and prompt you to login, but haven't had success personally.

Any further help would be appreciated!

---

