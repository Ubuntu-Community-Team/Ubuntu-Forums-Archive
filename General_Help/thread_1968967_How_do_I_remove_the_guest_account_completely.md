---
title: "How do I remove the guest account completely?"
date: 2012-04-29
forum: General Help
---

### Post by Zukaro on 2012-04-29
How do I remove the guest account entirely from Ubuntu 12.04?
I've already removed it from my login screen, but the account still exists (just isn't displayed at login anymore).

I've looked around on Google and the only things I find are how to remove it from the login screen.

---

### Post by strask on 2012-04-29
Ok, I just investigated this and it looks like when you use the guest option at the login screen, Ubuntu 12.04 creates a temporary user account named guest-XXXXX (where XXXXX is a bunch of random letters) and then deletes the account again as soon as the guest session logs out.

What account are you looking to remove? If it is a guest-blahblah account left over (perhaps the system crashed while a guest was logged in?) you can remove it with ```
sudo deluser <username>
```
You shouldn't have to specify the file deleting options to deluser because the ubuntu guest accounts are created with homes in /tmp, which should be cleared out at boot time anyway.

---

### Post by Zukaro on 2012-04-29
What I want to do is remove the guest account from being usable.  Like, I don't want there to be a guest account option on the start menu or at all (even after setting guest account to false in the lightdm.conf file it's still possible to use the guest account after logging in to my account; and I'd assume if you were to log in through a terminal it'd be possible to use the guest account again).

---

### Post by strask on 2012-04-29
> **Zukaro said:**
> (even after setting guest account to false in the lightdm.conf file it's still possible to use the guest account after logging in to my account
Oh really? Like from the menu with your name at the top that you use to switch users? Hmmm.

Well we need to figure out where that is configured then. I'm not sure where to start and don't have time right this minute to investigate, hopefully someone else has an idea.

> and I'd assume if you were to log in through a terminal it'd be possible to use the guest account again).

Given the way that it's working, I wouldn't assume that. Remember that when you aren't using the guest account, it doesn't exist. Something with root privileges needs to create a guest account before it can be used; this is done by the login screen. When you do it from the user-switch menu, I'm thinking it probably passes a request back to the login screen when your session suspends and the login screen is again responsible for doing this work. As far as I know, terminal sessions of any sort don't have any access to or control over the login screen.

---

### Post by uylug on 2012-04-29
This is a very common problem.

Assuming you're using the default login manager that comes with Ubuntu (Lighdm), you need to run:

```
sudo gedit /etc/lightdm/lightdm.conf
```And append this line to the end of the file:

```
allow-guest=false
```

Also, 'guests' can't login remotely to your computer as this would obviously be a security issue, no matter if the 'guest account' is enabled.

---

### Post by Zukaro on 2012-04-29
I've already edited the lightdm.conf file but it still appears under my username if I click on it (the thing that lets you quickly change sessions).  It's not really a big deal, but I'd rather remove it if I'm never gonna use it.  :P
Also, if I click logout the login screen shows the guest login again.  If I restart it's not there, but if I just logout and don't restart then the guest login is present again.

---

### Post by uylug on 2012-04-29
Yeah, you just need to reboot lightdm but if you do, all your programs will be closed.

Simply reboot your computer when you're ready, or run:

```
sudo /etc/init.d/lightdm restart
```( this will close any application you have running, if any )

**Edit:**
I got what you're saying. It must **be a bug**.

---

### Post by Zukaro on 2012-04-29
It's working now actually.  :P
Although lightdm never restarted (I got impatient after waiting for about 5 min so I just hit ctrl alt delete and restart).  But it's working now.

Thanks.  :)

---

### Post by rhdinah on 2012-04-30
Thanks uylug for your fix. It seems odd that with Unity we've taken some steps backwards from Ubuntu's 10.04 Gnome 2 where you could just check a checkbox to enable or disable the guest account from the user accounts' dialog window.

---

### Post by 0m3ns on 2012-07-13
Guys, I'm having trouble with this.

I have two Revo R3600 boxes. Both have Ubuntu 12.04 LTS installed via USB.

On the first machine, I was able to use the above command to edit the lightdm.conf but on the second, it either does nothing (ie nothing happens except the command box disappears), or it states that the files aren't found.

Any ideas?

---

### Post by 0m3ns on 2012-07-13
*hits head*

Found a slightly different command elsewhere:

**gk**sudo gedit /etc/lightdm/lightdm.conf which worked fine

---

