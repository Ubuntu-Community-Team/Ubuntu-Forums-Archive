---
title: "How to run handbrake?"
date: 2012-04-10
forum: General Help
---

### Post by x C0MMAND0 x on 2012-04-10
Here is what I did

```
sudo apt-add-repository ppa:stebbins/handbrake-releases
```

```
sudo apt-get update
```

```
sudo apt-get install handbrake-gtk handbrake-cli
```

I can't run them from terminal.  I try typing handb (and then tabbing), it won't complete commande, I can't run them.

When I re run the install, this is what I get

```
brent@Poseidon:~$ sudo apt-get install handbrake-cli 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
handbrake-cli is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 68 not upgraded.
brent@Poseidon:~$ 

```

And I can't run it

```
brent@Poseidon:~$ handbrake-gtk
handbrake-gtk: command not found
brent@Poseidon:~$ 
```

I'm guessing it installed somewhere else?  I'm not sure where, and also I don't know an easy CLI way to search for *handbrake*.*

Any ideas appreciated.

---

### Post by SeijiSensei on 2012-04-10
You should have gotten an icon and entry in the Multimedia section of the start menu.   On my Kubuntu installation, it's called "DVD Ripper" in the Multimedia section.

If you want to run it from the command line, the program is called "ghb" for "gtk handbrake" I believe.

```
ghb &
```

should open it in a separate window.

---

### Post by x C0MMAND0 x on 2012-04-10
That worked perfectly running "ghb" from terminal.  I don't have an icon in my multimedia tray, but I never use that anyways.

Thank you.

---

