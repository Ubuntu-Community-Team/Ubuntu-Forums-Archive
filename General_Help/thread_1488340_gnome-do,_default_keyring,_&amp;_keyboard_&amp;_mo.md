---
title: "gnome-do, default keyring, &amp; keyboard &amp; mouse clicks ignored"
date: 2010-05-20
forum: General Help
---

### Post by caughran on 2010-05-20
In other messages, there have been problems with a 10.04 update not listening -- it ignores typing and mouse clicks, though it does move the cursor, and things that proceed without help seem to be working.

Such was my problem, and I couldn't make any progress with it. So I created a new installation, which went well. Until I installed Gnome-Do. When I tried to actually use it, it asked for the password for the default keyring, and I was back in the rut again. The update froze on login -- while Do was waiting for keyring permission -- though I didn't realize that then.

I got out of the rut in the fresh install by using the live CD and renaming some of the Gnome-Do files to Gnome-Dont. (Apostrophe assumed.) Without Do, the problem didn't, and 10.4 now works.

But Do is a wonderful thing, and I miss it. Any ideas on how I can run it without the input problem? And how can I tell Ubuntu not to run Do with more elegance than the clumsy kludge I created?

The update is working fine on the desktop, with mostly the same software.

This is a Compaq notebook, AMD 64 (but running 32-bit Ubuntu), 3GB memory.

---

### Post by bg1256 on 2010-06-16
If I'm reading this correctly, you had to completely reinstall Ubuntu to fix this bug?

I'm encountering the same thing and am confused as to how to fix it.

---

### Post by caughran on 2010-06-16
> **bg1256 said:**
> If I'm reading this correctly, you had to completely reinstall Ubuntu to fix this bug?

I'm encountering the same thing and am confused as to how to fix it.

I reinstalled out of ignorance. The keyring application creates the problem, and gnome-do asks for the keyring. Here's a (clumsy) procedure, if I can remember.

- find your live disk and boot.

- gnome-do is in /usr/lib/gnome-do/. Delete essential files from there. The point is to uninstall gnome-do without keyboard or mouse.

- reboot to your hard-disk. Without Do, the keyring shouldn't pop up. If it does, it might be the network asking for the keyring. -- Rather than messing with anything that might call it, try similarly "uninstalling" the keyring applet.

- uninstall gnome-do from synaptic or command line.

- update the system; this is supposed to be fixed. That *should* end the problem.

- reinstall gnome-do

My question was how to do this more elegantly, as if one knew what needed to be done.

---

### Post by Curtos on 2010-07-05
> **caughran said:**
> I reinstalled out of ignorance. The keyring application creates the problem, and gnome-do asks for the keyring. Here's a (clumsy) procedure, if I can remember.

- find your live disk and boot.

- gnome-do is in /usr/lib/gnome-do/. Delete essential files from there. The point is to uninstall gnome-do without keyboard or mouse.

- reboot to your hard-disk. Without Do, the keyring shouldn't pop up. If it does, it might be the network asking for the keyring. -- Rather than messing with anything that might call it, try similarly "uninstalling" the keyring applet.

- uninstall gnome-do from synaptic or command line.

- update the system; this is supposed to be fixed. That *should* end the problem.

- reinstall gnome-do

My question was how to do this more elegantly, as if one knew what needed to be done.

I've been having the same issue with default.keyring and Gnome Do.  My system should be fully updated with all released updates (for 10.04). Is there something in your method that I'm missing?  

I just tried something new this morning that seems to have Do functioning, at least for the time being. Here's what I did (bare in mind that this I was in a slightly desperate state of mind whilst performing these actions, so feel free to point out if any steps are illogical or unnecessary):

Remove the default keyring.  In the terminal:

```
cd /.gnome2/keyrings/
rm default.keyring
```

Remove Gnome Do.

```
sudo apt-get remove gnome-do
```

Reinstall Do.

```
sudo apt-get install gnome-do
```

Replace the default keyring by navigating to Applications | Accessories | Passwords and Encryption Keys.  Click File -> New, select Password Keyring, name it "default" (no quotes), and click add. Set the password as your login password or you'll have to enter it at every login.  

Then it worked. Like magic. Does anything I did even make sense? Try it out and let us know if it works for you.  Previously, I have also set my default keyring to automatically unlock with Pam, though to no aid of my Do woes, so you may want to try that as well. Google it, mayhaps.

I do know an easier way to remove Gnome Do without breaking it via live CD, though.  When the system freezes at login due to the Gnome Do/keyring issue, enter a virtual terminal (ctrl+alt+F1), login as prompted, and kill Gnome Do. ```
pkill gnome-do
``` That will let you enter your keyring password and move on to removing, or what-have-you.  Sometimes this even lets Gnome Do function properly, but certainly not always.

Cheers,

Curtos

---

### Post by basthen on 2010-12-09
Well, it work for 1 time but not anymore. No fix then.

/*Not working
I know I am bringing back this thread back to live but this solution didn't work in 10.10 and I wanted to share my way.

Simply open the "Passwords and Encryption Keys" under System-Preferences. Under the Passwords tab, I right-clicked on Passwords:Login, unlock then enter your password. I had 2 entries related to gnome-do and I just deleted them. 

Easy like that. Hope it helps somebody.*/

---

### Post by Chocomochino on 2011-01-20
The same thing happened to me, to get my state back i uninstalled gnome-do using another terminal, but first i killed it.

using 10.10 amd64

---

