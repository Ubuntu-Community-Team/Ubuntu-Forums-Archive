---
title: "How can I hide or encrypt the wireless password so it can't be viewed?"
date: 2012-02-02
forum: General Help
---

### Post by link470 on 2012-02-02
Hello!  I'm setting up a few laptops with Ubuntu and I have added them to our wireless network.  The wireless key has been entered into a sample laptop in the NetworkManager and the connection works fine, however, I'd really like a way to disable the viewing of the key [which you can currently view by choosing the wireless tab in NetworkManager's Edit Connections window, highlighting the connection, choosing Edit, and clicking the check box for Show password].

Does anyone have a simple solution for either storing the password encrypted, or completely disabling that check box to view the password?  It doesn't have to be super complex, and I realize there are many of ways of still getting the password if a determined user was to sit down at the laptop.  But this is just to prevent the password viewing from being incredibly obvious.

Thanks!

---

### Post by lechien73 on 2012-02-02
Hi and welcome to the forums,

The procedure I have used is as follows:

[LIST]
[*]Create the connection to the wireless network while logged in as an administrator user (the user you created on installation).

[*]Check the "Available to all users" checkbox.

[*]Create other users as **Standard** users through the **User Accounts** applet.
[/LIST]

When they log in, they'll get access to the network, but won't be able to view any settings without the administrator password.

---

### Post by link470 on 2012-02-02
Thanks for your reply!

> **lechien73 said:**
> Create other users as **Standard** users through the **User Accounts** applet.

The problem with this is that the laptops will be used for testing linux software, and the users will be using the Ubuntu Software Center to download and try linux software.  My guess is that this is something they can't do from a standard user account.  Is that an incorrect assumption?  Can I still make them a standard user and have them install software from Ubuntu Software Center?

---

### Post by lechien73 on 2012-02-02
No, your assumption is entirely correct. I'm not sure if there's a way to limit users from accessing Network Manager, and still allow them to install software.

An alternative would be to change your wireless password after your testing has finished.

Alternatively, you can remove Network Manager altogether and use /etc/resolv.conf, /etc/networks, and other files to configure Internet access. I've never done this though, and don't know how to do it with WiFi.

---

### Post by link470 on 2012-02-02
> **lechien73 said:**
> Alternatively, you can remove Network Manager altogether and use /etc/resolv.conf, /etc/networks, and other files to configure Internet access. I've never done this though, and don't know how to do it with WiFi.
Ah, I was wondering about that.  I'll play with that and see what I can come up with!  Thanks for your help.

If anyone else knows how to do this or has any suggestions, please chime in!  I'll play with removing the network manager in the mean time though.

---

