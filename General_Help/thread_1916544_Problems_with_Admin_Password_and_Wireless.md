---
title: "Problems with Admin Password and Wireless"
date: 2012-01-28
forum: General Help
---

### Post by Tatious316 on 2012-01-28
[LEFT]Hi,

I'm completely new to Ubuntu, had to install it on to a broken windows OS desktop but loving it atm so if I can get the issues im facing sorted I may stick with it.

OK so, my wireless network firmware is missing, and I've googled and I know I have had to find a folder bw4-fwcutter or something which is hidden, so I was following instructions to type some code in to the terminal, then it came up asking for my password but wouldnt allow me to enter it, so I removed my password thinking that may remove the request, but it didnt, so I tried to readd the passowrd but now when I do it comes up asking for me to enter my admin password to unlock to make changes, but obviously, afaik no password exists, as I removed it.

I looked online about how to reset passwords and it said to boot in to recovery mode, however when I do so it it locked to limited read only, and I cannot scroll down to drop in to root shell, can anyone help me?
[/LEFT]

---

### Post by electrojustin on 2012-01-28
Let's start with:
What EXACTLY did you type into the terminal (perhaps a link the website you followed instructions from)?
Do you know the chipset of your wireless card?
What version of Ubuntu and kernel are you using?

Also, in Ubuntu command line, when prompted for passwords, you won't actually see what you type on the screen for security reasons-you won't even get the standard ***** or similar used on basically ever other password entering prompt in computing. Perhaps this is where the confusion arises?

---

### Post by Tatious316 on 2012-01-28
thanks for your reply, this is the link to where I was following the tutorial.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers")

my wireless is BCM4318

And I don't have the option to connect the desktop to the router wired, so I had to follow the B43 - No internet access steps (its in the content tree to the side)

Because I couldn't find the folder I didnt do the first bit and followed the instructions on how to find the folder, so I entered this code

```
~$ sudo mount -o loop /host/ubuntu/install/.fuse_hidden0000000400000001 /mnt
```it then came up asking for a password, and your password bit about not seeing any entry confirmation makes sense,  but now because I removed the password I dont knwo what to do, I've  tried to enter the password I did have for my user account and it doesnt  work, and now when I try to re-add a password to the account it wont  let me because I don't know the administrator password.

The version I am using is... 11.10 not sure what you mean by kernel.

---

### Post by Tatious316 on 2012-01-28
Sorry for bumping, but I really need urgent help with this, as I need access to the internet on this pc tonight, hope theres someone that can help me.

---

### Post by scheibenlosen on 2012-01-28
> **Tatious316 said:**
> Sorry for bumping, but I really need urgent help with this, as I need access to the internet on this pc tonight, hope theres someone that can help me.

 So, have you opened a terminal and typed "passwd" (no quotes) to set a new password for yourself? If not, do that and then see if everything else works like it's supposed to.

---

### Post by Tatious316 on 2012-01-28
hmm, thanks for the help on the password, that worked, but now its saying that the line of code i put in earlier is coming up as not existing, says no such file or directory.... Cant believe it is this hard to make my internet work.

---

### Post by scheibenlosen on 2012-01-28
> **Tatious316 said:**
> hmm, thanks for the help on the password, that worked, but now its saying that the line of code i put in earlier is coming up as not existing, says no such file or directory.... Cant believe it is this hard to make my internet work.

 You'll probably have to create at least the directory, and possibly the file. If you need to create the file, a blank one should do it, just for the sake of it being there.

---

### Post by grahammechanical on 2012-01-28
This is the bit in that link that concerns me:


> In case you couldn't find the folder, wubi keeps it as a hidden folder so you have to mount it. Follow these steps:

Have you installed Ubuntu using WUBI? Have you installed it inside Windows? If not, and you do not say that you have, then you should ignore that instruction. It does not apply.

You do realise, don't you, that you have made things harder for yourself?

These are the instructions that you should be following:

> b43-fwcutter is located on the _Ubuntu install media_ under ../pool/main/b/b43-fwcutter/ and patch is located under ../pool/main/p/patch/

You need to use the file manager to navigate to the live CD and look for a folder called **pool** and in that there is a folder called **main** and then a folder called **b** and from there to a folder called **b43-fwcutter** and there you will find the file **b43-fwcutter**

Now do this

> Double click on the package to install

Then use the file manager to navigate to a folder called **p** that is in the folder called **main** in there you will find a folder called **patch** and that has a file called **patch**. Now double click on it.

But note this:

> Note: In some versions (10.04 and 11.04 at least) there is not a /pool/main/p/patch/ If this file is missing then you don't need it. In this case you only need to install /pool/main/b/b43-fwcutter

Now do step 4

> Step 4.

Under the desktop menu System > Administration > Hardware/Additional Drivers, the b43 drivers can be activated for use.

Note: A computer restart may be required before using the wifi card.

Regards.

---

