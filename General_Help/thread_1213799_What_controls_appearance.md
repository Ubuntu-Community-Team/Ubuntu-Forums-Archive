---
title: "What controls appearance?"
date: 2009-07-15
forum: General Help
---

### Post by shelbyvision on 2009-07-15
A simple question, I think. My computer is having all kinds of problems, among them, I can't change the appearance at all. It now has some kind of generic Linux desktop, and if I go to System/Preferences/Appearance, it shows "Human" theme chosen for every option, which is what it had before it changed. The appearance preferences interface seem to be completely broken. It doesn't respond to any changes I try to make. 
HERE'S MY QUESTION: What program controls the interface for appearance preferences? 
Thanks,
Steve
Ubuntu 8.04 Hardy Heron

---

### Post by philinux on 2009-07-15
> **shelbyvision said:**
> A simple question, I think. My computer is having all kinds of problems, among them, I can't change the appearance at all. It now has some kind of generic Linux desktop, and if I go to System/Preferences/Appearance, it shows "Human" theme chosen for every option, which is what it had before it changed. The appearance preferences interface seem to be completely broken. It doesn't respond to any changes I try to make. 
HERE'S MY QUESTION: What program controls the interface for appearance preferences? 
Thanks,
Steve
Ubuntu 8.04 Hardy Heron

What did you do?

---

### Post by shelbyvision on 2009-07-15
> **philinux said:**
> What did you do?

I don't know. I just rebooted after some updates and everything was different. 
Steve

---

### Post by wojox on 2009-07-15
When you open Appearance Preference did you click the Customize button and see if everything lined up right in there?

---

### Post by shelbyvision on 2009-07-15
> **wojox said:**
> When you open Appearance Preference did you click the Customize button and see if everything lined up right in there?

Yes, Human is selected for everything there, but the desktop is not Human, it is some generic Linux desktop with blue borders, and any changes I try to make have no effect on the actual desktop. That's why I want to know what program controls it, so I can investigate it.
Steve

---

### Post by mcduck on 2009-07-15
Is gnome-settings-daemon running? What happens if you try to start it?

---

### Post by shelbyvision on 2009-07-15
> **mcduck said:**
> Is gnome-settings-daemon running? What happens if you try to start it?

I don't know. How do I start it?
Steve

---

### Post by mcduck on 2009-07-15
> **shelbyvision said:**
> I don't know. How do I start it?
Steve

Open a terminal and run "gnome-settings-daemon".

---

### Post by shelbyvision on 2009-07-15
> **mcduck said:**
> Open a terminal and run "gnome-settings-daemon".

Thanks. OK, I did that and this is what I got:

steve@laptop:~$ gnome-settings-daemon

** (gnome-settings-daemon:13601): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:13601): WARNING **: Could not acquire name
steve@laptop:~$

---

### Post by mcduck on 2009-07-15
> **shelbyvision said:**
> Thanks. OK, I did that and this is what I got:

steve@laptop:~$ gnome-settings-daemon

** (gnome-settings-daemon:13601): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:13601): WARNING **: Could not acquire name
steve@laptop:~$

Sounds like it's running, so that shouldn't be the problem. The next thing that comes to mind would be file permissions in your home directory. In case you've started any of your desktop applications with "sudo" you might have broken them. Of course if you are sure you haven't done that you don't need to check the permissions, but if in any doubt you should check that all setting files in your home directory are owned by your user.

---

### Post by shelbyvision on 2009-07-15
> **mcduck said:**
> Sounds like it's running, so that shouldn't be the problem. The next thing that comes to mind would be file permissions in your home directory. In case you've started any of your desktop applications with "sudo" you might have broken them. Of course if you are sure you haven't done that you don't need to check the permissions, but if in any doubt you should check that all setting files in your home directory are owned by your user.

No problems there.
Steve

---

### Post by shelbyvision on 2009-07-15
Is there no one who can answer my simple question? (What program controls the interface for appearance preferences?)
Steve

---

### Post by mcduck on 2009-07-15
> **shelbyvision said:**
> Is there no one who can answer my simple question? (What program controls the interface for appearance preferences?)
Steve

Actually, in a way, I already did. gnome-settings-daemon.

The thing is just that if it's running, and all your configuration files have correct permission, I just don't know what could be causing your problem.

---

### Post by shelbyvision on 2009-07-15
> **mcduck said:**
> Actually, in a way, I already did. gnome-settings-daemon.

The thing is just that if it's running, and all your configuration files have correct permission, I just don't know what could be causing your problem.

Thanks, mcduck. This has been a really perplexing problem. This is my third thread about it, and I've gotten nowhere.
Steve

---

### Post by Simian Man on 2009-07-15
Try making a new user and logging in with that.  If everything is fine, then one of the configuration files in your home directory got borked somehow.  If everything is not fine with a fresh user, then you have the more serious problem of some applications not working correctly.

---

### Post by shelbyvision on 2009-07-15
> **Simian Man said:**
> Try making a new user and logging in with that.  If everything is fine, then one of the configuration files in your home directory got borked somehow.  If everything is not fine with a fresh user, then you have the more serious problem of some applications not working correctly.

Thanks, I tried making a new user, and couldn't log in. It said "Incorrect username or password. Letters must be typed in the correct case." when I went to System/Administration/User Settings, the new name was not on the list, so I tried to add it again, and it told me that name already exists, try another one. Looks like catch-22 to me.
Steve

---

