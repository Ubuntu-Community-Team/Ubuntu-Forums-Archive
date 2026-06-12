---
title: "Thunderbird - Is this a bug?"
date: 2010-10-19
forum: General Help
---

### Post by sudoer541 on 2010-10-19
I just downloaded Thunderbird 3.1.4 and I think I found a security hole. 

Whenever I open Thunderbird, it does not ask me to authenticate my account (not asking for a password)  

Is this a bug/security hole or something? 

How can I force Thunderbird to ask me for my gmail password at startup?
Oh!!! and where can I report this security hole?

---

### Post by Troublegum on 2010-10-19
Thunderbird asks you if you want to store the password so that you don't have to enter it every time. That's hardly a security issue, but a feature.
Go to Tools -> Options -> Privacy -> Passwords -> View Saved Passwords and you should be able to clear your stored password.

---

### Post by cariboo on 2010-10-19
Instructions for the Windows version don't work when you are using the Linux version of Thunderbird. :)

Try Edit->Preferences->Security->Passwords, and click the Saved Passwords button.

**Edit** Moved to the support sub-forums ***again***. This isn't a Cafe querstion.

---

### Post by sudoer541 on 2010-10-19
> **Troublegum said:**
> Thunderbird asks you if you want to store the password so that you don't have to enter it every time. That's hardly a security issue, but a feature.
Go to Tools -> Options -> Privacy -> Passwords -> View Saved Passwords and you should be able to clear your stored password.


I tried this, but my account is still not secure.
When it prompts me for a password, I can always bypass it by clicking the cancel button and I cant still view my messages normally.

Is there a way to to make thunderbird display my messages only when a password/correct password is entered?

---

### Post by sudoer541 on 2010-10-19
> **cariboo907 said:**
> Instructions for the Windows version don't work when you are using the Linux version of Thunderbird. :)

Try Edit->Preferences->Security->Passwords, and click the Saved Passwords button.

**Edit** Moved to the support sub-forums ***again***. This isn't a Cafe querstion.


Eeek!:eek: your avatar looks scary lol.

btw where is the support area?

---

### Post by lovinglinux on 2010-10-19
You cans set a Master password in the preferences, so nobody can see your passwords.

You can also protect your Thunderbird profile (there is a Firefox version too) with the following extension:

[http://nic-nac-project.de/~kaosmos/profilepassword-en.html](http://nic-nac-project.de/~kaosmos/profilepassword-en.html)

I have tested it and it works as advertised. Nevertheless, it doesn't seem to be approved by Mozilla. I couldn't find it in AMO site.

Keep in mind someone with physical access to your machine and some skill can easily access your e-mails.

---

### Post by Troublegum on 2010-10-19
> **sudoer541 said:**
> I tried this, but my account is still not secure.
When it prompts me for a password, I can always bypass it by clicking the cancel button and I cant still view my messages normally.


That's the expected behavior. 
You can still read the mails you've already downloaded/fetched even if you cancel the download of new mails.

@cariboo907: thanks for the hint ;)
I don't have Thunderbird installed on my ubuntu box.

---

### Post by WorMzy on 2010-10-19
If you're worried about people reading your emails when you're not at your PC, get into the habit of locking your PC when you leave it unattended. That, as well as setting up good folder permissions, should keep out your average layman.

---

### Post by sudoer541 on 2010-10-19
I remember there was a way to force thunderbird to ask the user for a password.
If the user entered a wrong password, or if he clicked the cancel button, thunderbird would keep asking the user for a password or the user had the option to close the program.
I remember this was accomplished by using about:config and changing some strings here and there but I cant find the tutorial.

---

