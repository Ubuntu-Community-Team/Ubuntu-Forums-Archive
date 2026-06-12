---
title: "Can't login as Administrator"
date: 2012-01-20
forum: General Help
---

### Post by Scottty on 2012-01-20
Hello

I am trying to install VLC media player through the Ubuntu Software Centre and I get this message

Authenticate
To install or remove software you need to authenticate
Password: *******

and it won't work. 

a couple of day's ago I had gone into the system settings--> User Accounts

because I didn't want to have to login everytime I sat down.

I changed the password to None and 
Automatic login to on

Now I can't install anything.

Can you please let me know how to correct.

Scottt

---

### Post by 73ckn797 on 2012-01-20
> **Scottty said:**
> I changed the password to None and 
Automatic login to on

Now I can't install anything.

By "None" do you mean you left it blank?

> **Scottty said:**
> Authenticate
To install or remove software you need to authenticate
Password: *******

Are trying to enter a password?

---

### Post by coreychbt8295 on 2012-01-20
Had the same problem.  Try this: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Not having a password didn't work on my machine, so maybe just make it short.

---

### Post by Scottty on 2012-01-20
> 
By "None" do you mean you left it blank?


That is correct I left in blank

When I bring up User Accounts in the System Settings

I see my name Scott
Account type Administrator
Language English

Login Options
Password None (This actually says "None")
Automatic Login (Shows the word "ON")

Thank-you
scottt

---

### Post by 73ckn797 on 2012-01-20
> **Scottty said:**
> That is correct I left in blank

When I bring up User Accounts in the System Settings

I see my name Scott
Account type Administrator
Language English

Login Options
Password None (This actually says "None")
Automatic Login (Shows the word "ON")

Thank-you
scottt
So you are entering "None" as the password? or not entering anything? I am confused.
Which Ubuntu are you using. In 11.10 there is an option to not use a password in User Settings.

---

### Post by Scottty on 2012-01-20
> 
So you are entering "None" as the password? or not entering anything? I am confused.
Which Ubuntu are you using. In 11.10 there is an option to not use a password in User Settings.

That is what is beside the word Password

However if I click on the word "None" 
I get the option to enter the

Current password
New Password
Confirm Password

There are two buttons after that being

Cancel and Change. 

I have tried many different passwords but none are accepted. and it won't let me change them.

PS I'm using Ubuntu 11.10

Where is the option to not use a password in the user settings?

Thanks

scottt

---

### Post by Scottty on 2012-01-20
> Had the same problem. Try this: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Not having a password didn't work on my machine, so maybe just make it short.

I tried pressing Shift just before grub and did exactly the following

I typed ls /home
passwd myname

I was then prompted to type in a new password
and then asked to confirm password

I was then greeted with the following

Authentication token manipulation error

Password Unchanged

I then exited and started Ubuntu back up

I then tried to install VLC in the Software center and 

Recieved "Your authentication attempt was unsuccessful Please try again.

I'm thinking about reinstalling ubuntu 11.10. I just won't mess aroung with passwords next time.

Scott

---

### Post by 73ckn797 on 2012-01-20
> **Scottty said:**
> Where is the option to not use a password in the user settings?

See attached screenshot. The Action entry has password options. You must unlock the user info to make changes but that requires a password. This only affects login. :(
[IMG]http://ubuntuforums.org/home/frank/Documents/Passowrd.png[/IMG]

---

### Post by Scottty on 2012-01-22
I did a format reinstall of Ubuntu 11.10

Everything is good now. I won't screw around with passwords again.

Part of me is saying to myself well if I can't login neither can someone else which is good

The other side of me is a little disappointed that I could wreck my system so easy.

Would like to hear other opinions.

scottt

---

### Post by CharlesA on 2012-01-22
You needed to mount the drive as read/write before trying to change the password.

[http://askubuntu.com/questions/91188/authentication-token-manipulation-error](http://askubuntu.com/questions/91188/authentication-token-manipulation-error)

---

### Post by BotoxRehab on 2012-01-23
I'm having the same error right now, I cannot install any programs or anything, I do not want to do a fresh install. Is there anyway around this?:confused:

---

### Post by CharlesA on 2012-01-23
Check out the two links above - Boot into recovery mode, mount the local file systems and fix the password that way.

---

### Post by geddeth on 2012-05-10
In 12.04 LTS, I have configured my admin account to not have any password, as well as the other user accounts on the system.

After doing this, I received a message upon login about keyring authentication. From other threads, I learned that I could open "Passwords and keys" and set "Passwords: login" to "Use unsafe storage". That message then disappeared.

I am now shocked to find that **I cannot install software**, **nor set a new password for my user accounts** because I am unable to authenticate myself to the system.

I have used Ubuntu very briefly a couple of times over the years, and literally installed 12.04 yesterday. This is a major turnoff, and I **[COLOR="Red"]consider it a critical bug[/COLOR]**.

I have no problem booting directly to a shell and doing whatever to reset the password, but many others are sure to do what I did in order to sacrifice security for usability, and will not be interested in doing so.

If anyone has any information on related Launchpad bugs, please drop them here and I will provide info to the developers there.

---

### Post by CharlesA on 2012-05-10
So you created your admin account with no password and any other user account with no password.

Why?

Boot to recovery mode with the above instructions and set a password and go on with your life.

---

### Post by lisati on 2012-05-10
> **CharlesA said:**
> So you created your admin account with no password and any other user account with no password.

Why?

+1.
I would probably see the problem described a few posts back as a security feature rather than a bug. 

We could easily digress and discuss the merits of the various security models in place on the systems with a Windows and/or MS-DOS heritage, and thos on systems with a *nix heritage. The reality is that in these days of internet access, the decision to disable or remove the need for a password is something that shouldn't be taken lightly.

---

### Post by CharlesA on 2012-05-10
> **lisati said:**
> We could easily digress and discuss the merits of the various security models in place on the systems with a Windows and/or MS-DOS heritage, and thos on systems with a *nix heritage. The reality is that in these days of internet access, the decision to disable or remove the need for a password is something that shouldn't be taken lightly.

I was just talking about that sorta thing on IRC.. so +1

---

### Post by geddeth on 2012-05-10
I agree that my post does not warrant a discussion about security in general. 

But I don't see how you can ignore the fact that users can easily put their system in a state where they are unable to install software, re-enable their password and probably a slew of other items that require authentication.

Ubuntu should ask me when disabling my account passsword "YOU ARE ABOUT TO DISABLE 1) INSTALLATION OF SOFTWARE 2) RE-ENABLING YOUR ACCOUNT PASSWORD AND 3) ANY OTHER SYSTEM FUNCTIONS THAT REQUIRE AUTHENTICATION. ARE YOU SURE YOU WISH TO DO THIS?"

---

### Post by CharlesA on 2012-05-10
"Linux assumes you know what you are doing."

There is no reason to set a blank password when you only need it to login and do admin tasks.

---

