---
title: "&quot;Allow application access to keyring?&quot; tips"
date: 2009-12-28
forum: General Help
---

### Post by gifford.scott on 2009-12-28
This may belong in 'absolute beginner talk', but I've been a steady user of ubuntu and the gnome desktop for four months now, and the absolute opacity of the gnome-keyring-daemon and its seahorse GUI front-end has not yet failed to amaze me.  So, I thought I'd share my observations:

This post is intended to help those users (like me) who are befuddled by the "Allow application access to keyring?" query when setting-up or changing their wireless connections info.  It may also help users who use ubuntu as a dedicated single-user platform (and thereby configure automatic login w/no password prompt on start-up) and who therefore do not want to be prompted to 'Enter password for default keyring to unlock' *every* time they start-up ubuntu...

First off, what is this 'default keyring'?  A 'keyring' is linux terminology for a set of encryption keys that can be used to encrypt content, such as documents and passwords.  Keys are the numeric 'seeds' used to uniquely encrypt or decrypt content.  Under the gnome desktop (the default desktop for ubuntu), a set of keys are maintained for the user on an as-needed basis, for purposes such as ssh session initiation, transferring encrypted documents and (surprise!) wireless network access passwords.  Some clever individual decided to refer to this set or grouping of encryption keys as a 'keyring'.  So what is the *default* keyring?  This is gnome terminology for the implicit, automatic and apparently unavoidable storage of certain application passwords into the gnome keyring mechanism, such as wireless access passwords.

How to fix things:

You can access the gnome keyring through the 'seahorse' application (in keeping w/the nautical theme of the gnome apps).  Under ubuntu, seahorse is invoked by the menu selection: Applications>Accessories>'Passwords and Encryption Keys'.  (Note: Do not be tempted by the menu selection: System>Preferences>'Encryption and Keyrings'.  Apparently, this selection is provided by ubuntu just to confuse naive users... :) )

Again, you should begin by selecting Applications>Accessories>'Passwords and Encryption Keys'.  If you go to Help>About on the 'Passwords and Encryption Keys' window, you will see that this is 'seahorse', the gnome encryption key manager.  Inside the 'Passwords and Encryption Keys' window, select the 'Passwords' tab.  Under this tab, you should see, if you've set-up a wireless access password, a line that states: 'Passwords: default'.  This is the 'default keyring' referred to by those mysterious 'Enter password for default keyring...' and 'Allow application access to keyring?' queries that pop-up on the desktop like confetti when you change and/or mess with secure wireless network connections.

Once under seahorse, the 'Passwords and Encryption Keys' application, there are a few tricks that can be applied.  Click on the small triangle to the left of the 'Passwords: default' line and expand the listing of default password entries.  You can right-click on any entry below, to see the properties or delete a stored password.  If you click on the Properties of a stored password, you should be able to inspect the encrypted password by clicking on the small triangle to the left of 'Password:' and then clicking on the 'Show password' check box.  The encrypted password should then be represented by a long line of hexadecimal data, similar to '89dc929d2a0660fbf7062dd1585...'.  This hex string represents the *encrypted* version of the password / passphrase to be sent to the wireless network device on connection initiation - you will not see the actual data or text phrase you have typed into the 'Network Connections' password dialog box.

If you are having difficulties properly changing your wireless network password, it's usually simplest to delete the network password stored under 'Passwords: default', retrying the 'Network Connections' wireless password entry and allowing the gnome-keyring-daemon to store a new password for you.

If you wish to get rid of the 'Enter password for default keyring to unlock' dialog box on start-up, then there is another obscure trick to accomplish this: Under the seahorse 'Passwords' tab, right-click on the *small triangle* to the left of the 'Passwords: default' line.  In the right-click drop-down menu, select the bottom entry, 'Change Password'.  The 'Change Keyring Password' dialog box should then prompt you for the 'Old password' and allow you to enter a new 'Password'.  To get rid of the 'Enter password for default keyring...' prompt on start-up, *enter nothing* for the new 'Password' and click on the 'Change' button.  The dialog should prompt you w/a 'Store passwords unencrypted?' query, where you should click on the 'Use Unsafe Storage' button.

If you have forgotten your old password for the seahorse default keyring, then there is the tried-and-true nuclear option: Gnome seahorse stores the default keyring data in a user-accessible file in your home directory under .gnome2/keyrings.  If you use the File Browser, you'll need to select View>'Show Hidden Files' to see the .gnome2 directory.  Under the .gnome2/keyrings directory, you can delete the default.keyring file and then reboot, which will force seahorse to prompt you for a new password on the next attempt to start-up secure wireless connections.  To disable prompting for a password for default keyring access, just enter empty fields when a new default keyring password is requested.

Hope this helps...

---

### Post by whittaker007 on 2009-12-28
Thanks, that was driving me nuts! I found the solution to delete the default.keyring file and using a blank password a while ago, but I was never sure whether the blank password would affect only the network access, or whether it would expose any other password that used that keyring. I still don't know if that's the case or not, but using your method gives me a little more confidence that it only affects the network.

Thanks!

Scott

---

### Post by gifford.scott on 2009-12-29
FYI - I just updated from ubuntu 9.04 to ubuntu 9.10 (Karmic Koala), and it looks as though the 'Show password' option under the seahorse keyring manager has been fixed/changed: seahorse now shows the correct stored alphanumeric password string, instead of a line of hexadecimal data.  Perhaps another good reason to upgrade...

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by doas777 on 2009-12-29
not bad explaination. you should clean it up, add some screenshots, and post a howto

---

