---
title: "HELP! Network Manager Applet - /usr/bin/nm-applet"
date: 2009-08-31
forum: General Help
---

### Post by M!SF!TS on 2009-08-31
Hello,

    I ran into a recent problem, Due to no fault of my own stupidity... i posted my username & password, to my G-Mail account on this Forum, :-$ 

(let me tell you something about a user on this forum...   usr: tehrage   sent me a private message informing me of my mistake posting my user name and password on a post, if you ever run into this guy tell him how awesome he is... i was oblivious to my mistake and my personal info was out their for the whole world to see... and with out his heroic actions i would probally be another identity theft victim, internet fraud, and any kind of malicious criminal activities... he deserves some kind of UBUNTU FORUMS "MEDAL OF VALOR" award, or even a thread should be started, for hero's of the day!!!)

anyways, when ever i shutdown or reboot my computer, and log back in i get a keyring window that pops up, and i have to enter my old password in order for the Internet to connect... wtf ?  how do i change that password to Network Manager Applet, (found at /usr/bin/nm-applet) ? and how do i make it GO AWAY!!!!!!!! i dont want to have to enter 2 different passwds to connect to the 'net man!!!! it sucks... it has ruined my life!!!! okay im over reacting... but still its a huge issue !!!!!!!! it is annoying !!!!!!!! almost as annoying as these things !!!!!!!!!!!

HELP!

---

### Post by earthpigg on 2009-08-31
applications -> accessories -> passwords and encryption

---

### Post by ruth.mulenga on 2009-09-17
So far I have been on 2 threads which recommend the same thing System --> Preferences --> Encryption & Keyring, which I had already found for myself.

My problem is I still can't find a way to change the keyring.  When I go to Default key: the only option I have from the pop-up bar is None.  Prompt for a key.  

I am none the wiser how to actually do this.  Is there any scripts I can use in the terminal to help me?

THANKS

---

### Post by M!SF!TS on 2009-09-17
scripts in the terminal to do it ?  not that i know of.. to tell you the truth i forgot how to fix the problem once i fixed it... sooo... yeah i will try to reproduce it and post the steps i did... give me a little while...

---

### Post by mcduck on 2009-09-17
> **ruth.mulenga said:**
> So far I have been on 2 threads which recommend the same thing System --> Preferences --> Encryption & Keyring, which I had already found for myself.

My problem is I still can't find a way to change the keyring.  When I go to Default key: the only option I have from the pop-up bar is None.  Prompt for a key.  

I am none the wiser how to actually do this.  Is there any scripts I can use in the terminal to help me?

THANKS

1.Open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Passwords-tab

3. Right-click the "Passwords:login"-keyring & select "Change Password"

Now you can change the keyring password. If you use normal login set the password to same as your login password to unlock the keyring automatically. If you use automatic login leave the new password fields empty to remove the keyring password.

---

### Post by M!SF!TS on 2009-09-18
> **mcduck said:**
> 1.Open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Passwords-tab

3. Right-click the "Passwords:login"-keyring & select "Change Password"

Now you can change the keyring password. If you use normal login set the password to same as your login password to unlock the keyring automatically. If you use automatic login leave the new password fields empty to remove the keyring password.

Yeah, i just re did that problem, and i came up with the same thing mcduck did... i hope he solved it for you...

---

