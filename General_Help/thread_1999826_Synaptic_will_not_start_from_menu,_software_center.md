---
title: "Synaptic will not start from menu, software center will not install/remove programs."
date: 2012-06-08
forum: General Help
---

### Post by MeguhNad on 2012-06-08
Hey forum,

I've just freshly installed Xubuntu 12.04. I was using the update manager installing all the recommended updates and it asked me to reboot when it was done. After rebooting back in Xubuntu 12.04, I cannot launch Synaptic from the XFCE menu (under System) I also cannot install or remove any programs in the Ubuntu Software Center. If I try install VLC Media player for example, I click "install" and on the left of the install button where it says "free" it quickly says installing, then back to free. It does nothing. 

Synaptic does launch from this terminal code:

gksudo synaptic &

When it launches, the following appears in the terminal:  [1] 2540

But I want it working from the XFCE Menu.

Can anybody help? It's much appreciated.

---

### Post by wilee-nilee on 2012-06-08
> **MeguhNad said:**
> Hey forum,

I've just freshly installed Xubuntu 12.04. I was using the update manager installing all the recommended updates and it asked me to reboot when it was done. After rebooting back in Xubuntu 12.04, I cannot launch Synaptic from the XFCE menu (under System) I also cannot install or remove any programs in the Ubuntu Software Center. If I try install VLC Media player for example, I click "install" and on the left of the install button where it says "free" it quickly says installing, then back to free. It does nothing. 

Synaptic does launch from this terminal code:

gksudo synaptic &

When it launches, the following appears in the terminal:  [1] 2540

But I want it working from the XFCE Menu.

Can anybody help? It's much appreciated.

What happens if you run a regular update from the terminal any errors?

Or the vlc install from the terminal.

---

### Post by MeguhNad on 2012-06-08
> **wilee-nilee said:**
> What happens if you run a regular update from the terminal any errors?

Or the vlc install from the terminal.

Thanks for the reply. Yes, the terminal install works fine. No issues there.

---

### Post by wilee-nilee on 2012-06-08
> **MeguhNad said:**
> Thanks for the reply. Yes, the terminal install works fine. No issues there.

You can purge both the software center and synaptic and reinstall them I believe. There was a problem earlier with the software center opening in the development with a error in a particular file.

---

### Post by MeguhNad on 2012-06-08
> **wilee-nilee said:**
> You can purge both the software center and synaptic and reinstall them I believe. There was a problem earlier with the software center opening in the development with a error in a particular file.


Aha. This command lets me install software in the software center:
sudo software-centerVery confused.


What code would I use to purge and re-install both the synaptic package manager and the software center?

---

### Post by Enigmapond on 2012-06-08
> **wilee-nilee said:**
> You can purge both the software center and synaptic and reinstall them I believe. There was a problem earlier with the software center opening in the development with a error in a particular file.

Yes I would try that. Purge both and then re-install. Just know when you go to purge the software centre it will also say it's removing ubuntu-desktop...don't be alarmed as this is just a meta-package and does nothing on it's own and will re-install.

---

### Post by wilee-nilee on 2012-06-08
> **MeguhNad said:**
> Aha. This command lets me install software in the software center:
sudo software-centerVery confused.


What code would I use to purge and re-install both the synaptic package manager and the software center?

synaptic would be.
```
sudo apt-get purge synaptic
``````
sudo apt-get purge software-center
```then for both to reinstall
```
sudo apt-get install "app"
```I notice though that the software center has a file in .config in home you might try deleting that first and see if that fixes the software center problem.

---

### Post by MeguhNad on 2012-06-08
> **Enigmapond said:**
> Yes I would try that. Purge both and then re-install. Just know when you go to purge the software centre it will also say it's removing ubuntu-desktop...don't be alarmed as this is just a meta-package and does nothing on it's own and will re-install.

Just re-installed both and it has not fixed them. 

I've also just found out that I can't change my account type. 

As I can't change my account type, and I can install software when running the software center as "su" could this be an issue with my account?

If so, I have no clue what I can do to fix it.

---

### Post by wilee-nilee on 2012-06-08
> **MeguhNad said:**
> Just re-installed both and it has not fixed them. 

I've also just found out that I can't change my account type. 

As I can't change my account type, and I can install software when running the software center as "su" could this be an issue with my account?

If so, I have no clue what I can do to fix it.

You do not want to change the account type, is it an admin as of now?

---

### Post by MeguhNad on 2012-06-08
> **wilee-nilee said:**
> You do not want to change the account type, is it a admin as of now?

In User Settings, my account is called a "Custom account" I cannot change my account type or access the "Advanced setting" but I can change my password and account name.

---

### Post by wilee-nilee on 2012-06-08
> **MeguhNad said:**
> In User Settings, my account is called a "Custom account" I cannot change my account type or access the "Advanced setting" but I can change my password and account name.

Is this the account you had when you installed originally, that is a admin account and the one used in general safely.

Or is this a secondary account created.

We need to know if you have tweaked the account or this is one created by you or another for your use.

---

### Post by MeguhNad on 2012-06-08
> **wilee-nilee said:**
> Is this the account you had when you installed originally, that is a admin account and the one used in general safely.

Or is this a secondary account created.

We need to know if you have tweaked the account or this is one created by you or another for your use.

This is the only account on the system and the one I created when I installed Xubuntu.

---

### Post by wilee-nilee on 2012-06-08
> **MeguhNad said:**
> This is the only account on the system and the one I created when I installed Xubuntu.

I have not seen custom before, in an account name, so this is an area out of my pay range.

My **guess** is that something has caused a permission change.

You can run a update and install from the terminal though, so I am a bit stumped here to be honest.

This is a partitioned install right not a wubi install from windows?

---

### Post by MeguhNad on 2012-06-08
> **wilee-nilee said:**
> I have not seen custom before, in an account name, so this is an area out of my pay range.

My **guess** is that something has caused a permission change.

You can run a update and install from the terminal though, so I am a bit stumped here to be honest.

This is a partitioned install right not a wubi install from windows?

Yes this is in a seperate partiton.

---

### Post by wilee-nilee on 2012-06-08
Hard to say but it seems the account has been tweaked you might start a new thread addressing this, and have a reference to that in the header, to attract the people who know this area for help.

Just a guess here, but it would be nice to see all of this resolved for you.

---

### Post by Skara Brae on 2012-06-08
> **wilee-nilee said:**
> I have not seen custom before, in an account name, so this is an area out of my pay range.
(Just as a note of information and not wanting to hijack this thread: my only account here in Xubuntu 10.04, upgraded from 8.04, is also "*Custom*" (I can change it, though).
I checked this just now, out of curiosity. All works fine.)

---

### Post by lfla on 2012-11-07
This is due to the policy kit (polkit-1). 
The menu calls  synaptic-pkexec which is a bash script executing 
pkexec "/usr/sbin/synaptic" "$@"

Now when there are more sudoers pkexec prompts for the identity
used for authentication:

==== AUTHENTICATING FOR com.ubuntu.pkexec.synaptic ===
Authentication is required to run the Synaptic Package Manager
Multiple identities can be used for authentication:
 1.  Joe Doe,,, (jdoe)
 2.  Ubuntu,,,, (ubuntu)
Choose identity to authenticate as (1-2): 1
Password: 

A hack to get the rid of the problem is to use alacarte to modify the menu entry from 'synaptic-pkexec' to 'gksudo synaptic'

---

