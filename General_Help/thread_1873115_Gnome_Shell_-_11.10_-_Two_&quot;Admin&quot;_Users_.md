---
title: "Gnome Shell - 11.10 - Two &quot;Admin&quot; Users - GUI Override?"
date: 2011-10-31
forum: General Help
---

### Post by Roasted on 2011-10-31
I'm running Gnome Shell on Ubuntu 11.10. I have two administrator users on my system. Let's call them Fred, and Bob.

Bob was created first.
Fred was created second.

If I'm logged in as Fred and I do something in the GUI that requires a sudo-like override (such as hitting "unlock" on various menus in the system settings panel), it comes up with a familiar-ish root dialog box to override. Similar to when you open GParted, you have to authenticate, etc.

The thing is, in Gnome Shell, I cannot change the username it's authenticating as. Along with that, even if I'm logged in as Fred, "Bob" is the user in the list. Using Fred's password is a no go. Using Bob's password works fine.

But again, I'm logged in as Fred. Fred is the current user. Fred is an administrator. I want to authenticate as Fred. Not Bob.

A quick look at Unity shows the same task brings me a dialog box with a drop down menu, so I can select between Fred and Bob. Likewise, the proper user is already defaulted in the menu to begin with.

Any insight?

EDIT - Just curious. Is this a Gnome Shell thing? Ubuntu thing? Would Fedora with Gnome Shell likely do the same thing?

---

### Post by Pater Phil on 2011-11-04
I've posted a fix below, but I also have answers to your questions.

> **Roasted said:**
> 
EDIT - Just curious. Is this a Gnome Shell thing? Ubuntu thing? Would Fedora with Gnome Shell likely do the same thing?

For what it is worth, this behavior is frustrating me as well. 

The problem appears to be upstream Gnome, and a bug has been  reported [here. You can find a link to another bug report there that has more information plus a reported fix. The fix is located [URL="http://anti.teamidiot.de/nei/2011/10/gnome_3_authentication_require/"]here]("https://bugzilla.gnome.org/show_bug.cgi?id=659310"). I've changed the extenstion to this guy's patch file and uploaded it here for convenience.

Here are the steps you need to take:
1.) Download the attached diff file, polkit.txt.

2.) Backup /usr/share/gnome-shell/js/ui/polkitAuthenticationAgent.js (I just copied it to my home directory).

3.) Then patch.

4.) Logout and Login

Assuming you've downloaded the patch file to ~/Downloads, then all you need to do is this:

```

cp /usr/share/gnome-shell/js/ui/polkitAuthenticationAgent.js

sudo patch /usr/share/gnome-shell/js/ui/polkitAuthenticationAgent.js  ~/Downloads/polkit.txt

```

---

### Post by Roasted on 2011-11-05
What does the fix provide the end user? Do you have the ability to choose what user you override as, or does it just auto-fill in whatever user is currently logged in to the user box?

---

### Post by Pater Phil on 2011-11-09
> **Roasted said:**
> What does the fix provide the end user? Do you have the ability to choose what user you override as, or does it just auto-fill in whatever user is currently logged in to the user box?

I haven't attempted to access in admin areas as a regular user, so I cannot say what happens as far as that is concerned. However, for an account with sudo privileges, it will simply ask for that user password instead of the first account created.

---

