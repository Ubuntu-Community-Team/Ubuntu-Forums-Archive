---
title: "Login keyring box"
date: 2010-05-01
forum: General Help
---

### Post by singercs on 2010-05-01
I am very impressed with 10.04, that is once you have it installed and don't mind the wait to boot, one thing that came up this morning when I booted it up was a box with the message that my login key ring didn't work and wanting me to enter my password but goes away when I do, I have it set to auto login but still see this message, it didn't do this through a dozen or so log ins after the install.

---

### Post by P4man on 2010-05-01
It is *because* you set it to autologin that you get a request to enter your password to open the keyring.

Keyring stores your passwords for things like your email, IMs, networks, etc. Passwords are stored on your drive encrypted, and the encryption key needed to decode them, is your keyring password (usually the same as your login password, unless you changed it). If you enable  autologin, the keyring can not be opened, because you have not given the decode key, hence the passwords cant be unencrypted for applications to use. This is by design.

The only way around that is either not using the keyring, and thus not storing your passwords or  storing your passwords unencrypted on your drive, by settings a blank keyring password. I wouldnt recommend that though,  because that would allow anyone with physical access to your pc and some knowledge or tool to read your passwords. From any account, or from a livecd.

long story short, disable autologin. If you are going to enter a password, it might just as well be when logging in. Unless you dont mind a whole lot of insecurity.

---

### Post by singercs on 2010-05-01
Thanks, that's what I did and now it solved it..
other than that, no big issues and have a great one..

---

### Post by Neobuntu on 2010-05-01
This is broken; for those of us who want auto login. I wasn't aware that Ubuntu/Gnome doesn't address such basics. Is this geek rule? Thou shalt not auto login?

---

### Post by mixmaster on 2010-05-01
> **Neobuntu said:**
> This is broken; for those of us who want auto login. I wasn't aware that Ubuntu/Gnome doesn't address such basics. Is this geek rule? Thou shalt not auto login?

No, it is not a geek rule it is a matter of basic security.  Nor is it broken - a few posts up someone explained how to avoid having to enter any passwords.  If you have a machine with nothing of value on it or you are happy that you have sufficient physical security to prevent any unauthorised activity then go down that route.  Personally I'm willing to type in a password occasionally for the added security it brings.

---

### Post by P4man on 2010-05-01
> **Neobuntu said:**
> This is broken; for those of us who want auto login. I wasn't aware that Ubuntu/Gnome doesn't address such basics. Is this geek rule? Thou shalt not auto login?

If you want autologin you can have it. If you want that autologin to also expose all the passwords in your keyring to anyone who can touch your PC, then you can have it. What you *cant* have is a secure desktop with your passwords in the keyring saved securely without having to enter a password to access them. If you think about it, it kinda makes sense, no?

---

### Post by P4man on 2010-05-01
BTW, your wifi password can also be stored in the keyring, but maybe you dont want that. You can have network manager store the wifi password in clear text, so its readable to anyone,  but then network manager doesnt require the keyring to be open. That way you can use the keyring to store more sensitive passwords like for email (and requiring your user password to access those), and still be able to login and access the internet without having to enter a password. 

Its really not a design flaw, its a lack of understanding I think.

---

### Post by halfsoul on 2010-05-01
> **P4man said:**
> BTW, your wifi password can also be stored in the keyring, but maybe you dont want that. You can have network manager store the wifi password in clear text, so its readable to anyone,  but then network manager doesnt require the keyring to be open. That way you can use the keyring to store more sensitive passwords like for email (and requiring your user password to access those), and still be able to login and access the internet without having to enter a password. 

Its really not a design flaw, its a lack of understanding I think.

So are you saying that the reason it asks for my keyring is because it needs to use the wifi password when I access the internet?  If so, two questions:
1. I have wifi, but I use a LAN connection.  So why is it required?
2. Why did this behavior change from 9.10?

[rant]
Also, it irritates me that Linux peoples' typical response is "you have to do it for security".  I am trying hard to switch over from Windows, but some things about Linux are difficult for my wife to accept.  Users, permissions, & passwords/security being the crux of it.  She doesn't want to have to enter a password to login, or edit permissions to be able to open a file that we both use.  She doesn't want to have to type things into a terminal, and she doesn't want to see cryptic messages about keyrings when she opens a web browser.
[/rant]

---

### Post by Kirky_D on 2010-05-01
> **halfsoul said:**
> So are you saying that the reason it asks for my keyring is because it needs to use the wifi password when I access the internet?  If so, two questions:
1. I have wifi, but I use a LAN connection.  So why is it required?
2. Why did this behavior change from 9.10?

[rant]
Also, it irritates me that Linux peoples' typical response is "you have to do it for security".  I am trying hard to switch over from Windows, but some things about Linux are difficult for my wife to accept.  Users, permissions, & passwords/security being the crux of it.  She doesn't want to have to enter a password to login, or edit permissions to be able to open a file that we both use.  She doesn't want to have to type things into a terminal, and she doesn't want to see cryptic messages about keyrings when she opens a web browser.
[/rant]

Use windows? It's clearly a better option for you and your wife right now. It's all about choice, you have one, which is what linux brings. If you don't like it, choose something different, or change it to suit your needs.

---

### Post by P4man on 2010-05-01
> **halfsoul said:**
> So are you saying that the reason it asks for my keyring is because it needs to use the wifi password when I access the internet?  If so, two questions:
1. I have wifi, but I use a LAN connection.  So why is it required?

I dont know which passwords you have stored in the keyring. Wifi is a common complaint, so i just guessed, but it could be its asking the keyring password for your instant messenger, checkgmail or any app where you stored the password in the keyring and that runs at boot. I cant answer that for you.

> 2. Why did this behavior change from 9.10?

AFAIk, it didnt. Maybe you are using the gwibber thing or ubuntu one now, and storing either password in the keyring, and  you didnt do so in 9.10?

> 
[rant]
Also, it irritates me that Linux peoples' typical response is "you have to do it for security". 

Well, maybe we like security :) there is a reason on linux you neednt worry about viruses and malware, but it comes at a price. Properly configured, and once you understand how things work, you will find that price is not very high, but there is always a trade off between security and usability. 
> 
 I am trying hard to switch over from Windows, but some things about Linux are difficult for my wife to accept.  Users, permissions, & passwords/security being the crux of it.  She doesn't want to have to enter a password to login, or edit permissions to be able to open a file that we both use. 

She doesnt have to. But you do have to set up the network sharing properly once. How did you set it up?f

>  She doesn't want to have to type things into a terminal,

Id challenge anyone to find 2 common tasks that require a terminal. But at the same time, i will alnost always give terminal command in the forum. Why? Because its easier for me to give a short command than describe a long GUI approach that differs from PC to PC (and from language to language, and between ubuntu and kubuntu and mint and wether or not you have docky installed). 

The terminal is fast and easy to get help and allow you to copy paste the result. Doing it the gui way would require long explanations and screenshots.

But if there is something you want to know how to achieve through a gui, feel free to ask, almost anything can be done through the gui as well (though some things may require installing a gui tool, but you can install that through the gui as well)

>  and she doesn't want to see cryptic messages about keyrings when she opens a web browser.


Ask her if she wants anyone in your house to be able to read her emails, send fake twitters and check her facebook account. Entering a password when logging in really seems like a small price to pay to avoid that, but if she disagrees, we can set a blank password on the keyring. But do ask her first what she prefers.

---

### Post by halfsoul on 2010-05-01
> **P4man said:**
> Maybe you are using the gwibber thing or ubuntu one now, and storing either password in the keyring, and  you didnt do so in 9.10?
Hmmmm, I bet that's it (Ubuntu One) -- I'll look into that.  Is it really too much to ask that I shouldn't have to play guessing games about what program, process, or activity is asking for access to the keyring?  This is where I consider it to be "broken".


> **P4man said:**
> Well, maybe we like security :) there is a reason on linux you neednt worry about viruses and malware, but it comes at a price. Properly configured, and once you understand how things work, you will find that price is not very high, but there is always a trade off between security and usability.
Don't misunderstand, I'm in the same camp.  If were the only one using the computer I'd have it configured much differently.  My rant was about people giving their opinions and trying to talk others out of their question instead of helping them to accomplish their goals and answering their questions.


> **P4man said:**
> Ask her if she wants anyone in your house to be able to read her emails, send fake twitters and check her facebook account.
If there's someone we don't trust in our house and on the computer then there's a bigger problem than just computer access.
:)

She doesn't know it yet, but someday she'll be switched over to Linux and we will be separate users with decent security configurations.  It's gotta come in baby steps though, which is why I don't like getting into the "you should do your security this way" conversation.

---

### Post by P4man on 2010-05-01
> **halfsoul said:**
> Hmmmm, I bet that's it (Ubuntu One) -- I'll look into that.  Is it really too much to ask that I shouldn't have to play guessing games about what program, process, or activity is asking for access to the keyring?  This is where I consider it to be "broken".

yeah it should tell you. You sure it does not? anyway you can see what passwords the keyring manager manages for you in applications > accessoiries > passwords and encryption
> 
Don't misunderstand, I'm in the same camp.  If were the only one using the computer I'd have it configured much differently.  My rant was about people giving their opinions and trying to talk others out of their question instead of helping them to accomplish their goals and answering their questions.

I can sympathize with those people. really. I spend a fair amount of time helping so I know exactly why they do that. Too often a new linux user that just installed ubuntu and gets confronted with password prompt to install something will ask "how do I become root". If you tell him how, you are not helping him and you will make life for other posters here a lot harder because the next day he will have logged in as root and  post with 514 different issues about no longer being able to log in to his account, not owning his home folder, Xauthority errors and ranting how ubuntu sucks. Provided no one hacked his computer by then by running firefox as root.

> If there's someone we don't trust in our house and on the computer then there's a bigger problem than just computer access.

Well good for you. But do keep in mind the PC is connected to a a few hundred million other PCs, so make sure you know exactly what security features you are disabling and how it affects you.

---

### Post by halfsoul on 2010-05-01
> **P4man said:**
> yeah it should tell you. You sure it does not? anyway you can see what passwords the keyring manager manages for you in applications > accessoiries > passwords and encryption

Yeah, it just says Enter password for keyring 'default' to unlock.  Thanks for the info about the Passwords, confirmed it is Ubuntu One.


> **P4man said:**
> I can sympathize with those people. really. I spend a fair amount of time helping so I know exactly why they do that.
I suppose that's perfectly reasonable.  Thanks again for your help.

---

### Post by leorolla on 2010-06-29
If your computer is physically protected and you didn't do anything special with your Ubuntu Desktop install, all the important ports are closed and you are safe.

But please keep in mind the following:
 
If someone will ever possibly have physical access to your computer having bad intentions, they will be almost able to read through your soul.

Whatever you can do with your computer, anyone else can do.

If you can access your taxes, anyone else can do.
If you can access your finances, anyone else can do.
 If you can access your porn, anyone else can do.
 If you can access your social security number, anyone else can do.
If you can access your friend's names and phone numbers, anyone else can do.
 If you can access your passport number, anyone else can do.
 If you can access your e-mails with this cute girl you met on the street, anyone else can do.
If you can send a message to your boss having your name on the Sender field, anyone else can do.

If you can do all the above but only after having typed a short-but-yet-hard-to-guess password, anyone else can do.
In practice it means that anybody rather than you will be stuck on the password prompting stage.

That's all about it:
The knowledge of a short-but-yet-hard-to-guess password is what distinguishes you from anybody with possession of your PC.
Ingenious, uh?

Ubuntu gives you the choice.
   
  After 5 minutes of clear explanation, your wife will understand this.

If you don't care about her privacy, just create a user with no-password  login for her.
Then set the keyring password to empty:  Applications->Accessories->Passwords->Passwords:login->right-click->ChangePassword->Blank

I personally prefer having a password between me and the computer:

 There is no other reliable way the computer will know for sure that it  is me in front of it. There is no reliable way the computer will care  about it in first place.
I live in a city where from time to time houses do get broken into.
I lend my computer to guests I don't know that well.
I lend my computer to dear fellow colleagues whose latest article I am  anonymously refereeing.
I lend my computer to my curious mother with whom I don't really intend to share every detail of my life.
And the worst is that I have laptops that I bring with me everywhere in  the world... they don't stay locked in my bank safe.

---

