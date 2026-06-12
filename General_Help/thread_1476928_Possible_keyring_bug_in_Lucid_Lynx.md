---
title: "Possible keyring bug in Lucid Lynx"
date: 2010-05-08
forum: General Help
---

### Post by krippa on 2010-05-08
I think I have found a bug in Lucid Lynx but I wanted to ask around before filing a bug report. What I am trying to do is to set up a computer for a non-technical person. So I dont want the login screen in the beginning and I dont want it to ask for a keyring password.

First of all I think it was weird that Lucid automatically sets the keyring password to the user password so when I added a wireless key it asked me for keyring password without having defined one. This might make it easier for a lot of users so this is fine. I however dont want even this security, I want an empty keyring password so the user gets auto logged-in and connected to wireless network  without specifying a password.

After some googling I just deleted the keyring files from ~/.gnome2/keyrings and rebooted. Now when I get in I get asked for wireless password again and then to specify the keyring password. I leave it blank to use unencrypted storage. Now I thought it was setup the way I want it but no.. When I reboot it asks me for the wireless key and keyring password every time! I set it to nothing, reboot and its gone. Very frustrating! Also, if I let it go into sleep mode, wake it up and enter password to unlock it it will ask the password and automatically have set the keyring password the user again. I supect these are 2 symptoms of the same problem... Non-secured keyring is never saved.

Has onyone been able to set an empty keyring password and made it stay that way in Lucid?

Kris

---

### Post by ibrahim.k on 2010-05-08
I think you should Go to the Applications > accessories > Passwords and encryption keys.

Choose a new keyring password.

---

### Post by krippa on 2010-05-08
> **ibrahim.k said:**
> I think you should Go to the Applications > accessories > Passwords and encryption keys.

Choose a new keyring password.

Yep, that way it seems to work, thanks

---

### Post by chappajar on 2010-05-09
The other option is to not use the keyring:

  - System > Preferences > Startup > untick keyring 
- In ~/.gnome2/keyring delete all files 
- Restart 

 No more password dialogues on startup :)

---

### Post by _0R10N on 2010-05-09
It's my understanding that Ubuntu asks for the keyring password when the user password and the keyring password are not the same. Is this correct?

---

### Post by krippa on 2010-05-09
I believe that is what happens yes. 

In the middle of this I also found another way which is very useful, to tick "available to all users" I dont know where the keys are stored in this case but there is no keyring password dialog and it will connect to wireless network BEFORE you even log in.

Cheers
Kristofer

---

### Post by skualos on 2010-05-09
I had more or less the same problem:

I wanted to get rid of typing the keyring password each time the system booted up.

After deleting all files in the ./gnome2/keyring folder I rebooted the system.

It asked for my wifi password an then for a new keyring password, wich I left blank.

I thought the problem was solved, but when I restarted the system, it asked again for wifi password, and to set a password for the keyring again.

In the keyring folder, I saw that I had a file created for each time I rebooted the system and set up a new keyringpassword:

padrão.keyring
padrão_1.keyring
and so on (I use the PT-BR pack, padrão = default)

By browsing the web I found this topic: 

[https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/560581](https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/560581)

It seems that keyring manager can't read the files with accents (French distro seems to have the same problem with the par_défault.keyring file)

I could solve the problem by deleting all keys in keyring folder, going in the keyring manager. You have than the option to create your own network and applications keyring.

I created one with no accents on its name and left password in blank, then set it to be my default keyring.

Rebooted the system, was asked for the wifi password, and this time was not asked for the keyring password.

In my keyring folder I have now to files:
one with the name I gave, and wich contains my wifi and other passwords not encrypted, and another one named default, saying that the first file is my default keyring.

Sorry if I can't explain better, but english is not my native language, I'm really new to linux, and have a broken arm so I'm typing with just one hand!

Hope I could help.

---

### Post by chappajar on 2010-05-10
> **skualos said:**
> I had more or less the same problem:

I wanted to get rid of typing the keyring password each time the system booted up.

After deleting all files in the ./gnome2/keyring folder I rebooted the system.

It asked for my wifi password an then for a new keyring password, wich I left blank.

I thought the problem was solved, but when I restarted the system, it asked again for wifi password, and to set a password for the keyring again.
...
You should have also removed the keyring from startup in preferences.

---

