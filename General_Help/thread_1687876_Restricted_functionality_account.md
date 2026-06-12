---
title: "Restricted functionality account?"
date: 2011-02-14
forum: General Help
---

### Post by Mrich1976 on 2011-02-14
Ok...I'm still new to this. I just installed Ubuntu 10.10 desktop on a computer.

I am accessing it remotely through NoMachine.

I would like to set up a restricted account for my son to use. He's 5 years old, and finds the Terminal amusing.

However, I don't want him to access the terminal, because he does something with exclamation marks, and it slows the machine down while it's processing, and he gets upset. That, and I don't want him accidentally doing something he shouldn't.

So, is there a way I can restrict what he enters in the Terminal? I've been teaching him very, very basic programming, some of which requires the terminal (I think).

Also, would there be a way I could set the account up where he can't delete anything?

I'd basically just want an account that allows read/execute, and write but not delete.

I'm a newbie in Linux, so please forgive me if some of this can't be done. I've installed it on a custom box that has a 2.7 GHz AMD Processor, 2 GB of RAM, and a 500GB SATA Hard Drive.

It's mainly for learning purposes right now, but I could definitely see myself using it for more serious things (things I will discuss in another thread).

Any help or thoughts on this would be very, very appreciated.

---

### Post by Mrich1976 on 2011-02-15
Anyone know how to do any of this?

---

### Post by sydbat on 2011-02-15
You could simply hide the terminal (right click anywhere on the "Applications, Places, System" area, then choose "Edit Menus").

Or you could set up a new limited account under System > Administration > Users and Groups.

Finally, unless your son has your password, there is little he can do to system files...but he could delete things in /home. Setting up that separate limited account will let him do whatever he wants in his own user space without affecting your /home.

---

### Post by Mrich1976 on 2011-02-15
I may take that route, but the problem is, I like the terminal being in the menu.

I don't know if Linux has the capability to adjust the menu based on the permissions of the logged in user. That's ideally what I'd like. This way, my wife and I can have access to the terminal, but we could set up an account for my son so that he cannot, without me having to do something (put in a password, for instance).

Even better, if the terminal is there, but I can restrict what actually functions in the terminal.

I don't know what he's doing, but he's putting in words with exclamation marks (like foo!!!!!!!!!!!!!!!!!!!!!!!!!!), and it's printing things on the screen. I guess the ! is a shortcut for print, or something. But it's taking a bit to function, and he gets a little impatient waiting on it.

---

### Post by sydbat on 2011-02-15
> **Mrich1976 said:**
> I may take that route, but the problem is, I like the terminal being in the menu.

I don't know if Linux has the capability to adjust the menu based on the permissions of the logged in user. That's ideally what I'd like. This way, my wife and I can have access to the terminal, but we could set up an account for my son so that he cannot, without me having to do something (put in a password, for instance).

Even better, if the terminal is there, but I can restrict what actually functions in the terminal.

I don't know what he's doing, but he's putting in words with exclamation marks (like foo!!!!!!!!!!!!!!!!!!!!!!!!!!), and it's printing things on the screen. I guess the ! is a shortcut for print, or something. But it's taking a bit to function, and he gets a little impatient waiting on it.Like I mentioned, create a new user with limited permissions, then hide the terminal for that user. Open gedit (or some other text app) and let your son go nuts with it, instead of the terminal.

Then, when you or your wife log into your main account, everything will be as you want it. DO NOT allow your son to use your account, or everything will just continue to go around in circles.

That's my $0.000002

---

### Post by Mrich1976 on 2011-02-15
Awesome.

That's a lot more clear.

I'll just set up an account for him that doesn't have Terminal access. That makes it much easier.

I'll check this out, and if this resolves the issue, I'll come back and mark it as resolved.

---

