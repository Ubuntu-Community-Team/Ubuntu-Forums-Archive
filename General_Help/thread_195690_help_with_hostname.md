---
title: "help with hostname"
date: 2006-06-13
forum: General Help
---

### Post by richardhp on 2006-06-13
I had trouble re-installing Breezy after having busted it somehow although I'm not sure how.

In may haste of having to run the install program several times I set the default computer name to ubuntu. I wanted to change it back to what I had before and read the all that needed to be done was to type:

sudo hostname xxxx

Which it successfully changed but I didn't know I had to add the new hostname to /etc/hostname so now whenever I try to sudo anything it comes up with an error saying it can't find hostname and it looks something like this:

sudo: unable to lookup host richpc via gethostname()

As you can see I am in quite a predicament as it won't let me add my new hostname to /etc/hostname because that requires root access. I hadn't yet set up a root account and don't know what the default root password is so I am unable to login as root, can't sudo to add hostname, because the hostname isn't there.

It seems like a vicous circle and I was wondering if there was any way out without going through all the bother of re-installing which I have already had to do 4 times today.

---

### Post by DJ Scribblinni on 2006-06-13
reinstalling 4 times, you go man!  Anyways, are you using GNOME?  If you are here are a couple of steps that you can use using the GUI to change the hostname,     
* System -> Administration -> Networking
* Network settings 

General Tab -> Host Settings -> Hostname: Specify the computer name

Then restart.  Now you mentioned using root access to get to etc/hostname, you as the user should be able to access that file using your password.  The root user is disabled by default when Ubuntu is installed.  I hope that points you in some sort of direction.

---

### Post by richardhp on 2006-06-14
Well the problem was, it wouldn't let me Sudo anything and the owner of /etc/hostname is root so i couldn't access it.

Network settings worked a treat anyway so thanks.

---

