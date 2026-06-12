---
title: "Trying to install Java - Follwing the HowTo but ran into a weird problem"
date: 2006-04-01
forum: General Help
---

### Post by gurjit on 2006-04-01
Here is the link to the HowTo I followed to install Java:

[http://ubuntuforums.org/showthread.php?t=70428]("http://ubuntuforums.org/showthread.php?t=70428")

I've done everything up until the point where you type in the following commands:
**[COLOR="Red"]fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin[/COLOR]**

And this is what happens when I go to the directory in which the jre-1_5_0_06-linux-i586.bin file was downloaded and run the above command:

**(notice that I do [B]not** use sudo as it says in the HowTo)[/B]
> 
gurjit@UBUNTU:~/Desktop$ fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin
You are real root -- unfortunately, some Java distributions have
install scripts that directly manipulate /etc, and may cause some
inconsistencies on your system. Instead, you should become a
non-root user and run:

fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin

which will allow no damage to be done to your system files and
still permit the Java distribution to successfully extract.

Aborting.
gurjit@UBUNTU:~/Desktop$

I am running these commands from the Terminal program located in Applications>Accessories>Terminal (I don't know if this help but I thought I'd say it anyways)

On a side-not I'm new to Ubuntu and I'm finding out that it really is the best way to go compared to Windows, it has a few problems initially but its nothing that can't be fixed without some research or help from the Ubuntu forums.

If anyone has any ideas please feel free to post them i will gladly try them out.
Thanks in Advance

Gurjit Bains

---

### Post by mstlyevil on 2006-04-01
[QUOTE=gurjit]Here is the link to the HowTo I followed to install Java:

[http://ubuntuforums.org/showthread.php?t=70428]("http://ubuntuforums.org/showthread.php?t=70428")

I've done everything up until the point where you type in the following commands:
**[COLOR="Red"]fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin[/COLOR]**

And this is what happens when I go to the directory in which the jre-1_5_0_06-linux-i586.bin file was downloaded and run the above command:

**(notice that I do [B]not** use sudo as it says in the HowTo)[/B]


I am running these commands from the Terminal program located in Applications>Accessories>Terminal (I don't know if this help but I thought I'd say it anyways)

On a side-not I'm new to Ubuntu and I'm finding out that it really is the best way to go compared to Windows, it has a few problems initially but its nothing that can't be fixed without some research or help from the Ubuntu forums.

If anyone has any ideas please feel free to post them i will gladly try them out.
Thanks in Advance

Gurjit Bains[/QUOTE]

You need to log out of root and run it again as a normal user using sudo. That is why you are getting the error message. After that you can log back in as a root user.

---

### Post by gurjit on 2006-04-01
Sorry this might sound stupid, but how do you log out of root?

Thanks Alot For Your Reply
Gurjit Bains

---

### Post by mstlyevil on 2006-04-01
[QUOTE=gurjit]Sorry this might sound stupid, but how do you log out of root?

Thanks Alot For Your Reply
Gurjit Bains[/QUOTE]

If you are just logged in on the terminal, just type in exit and hit enter. Then you will be the sudoer user once again. If you logged in as root at the start screen, just log out and log in as the user you originally set up during installation.

---

### Post by gurjit on 2006-04-01
I am using the account that i used to install Ubuntu with? If you need more info please tell me what i can do to help you.

Thanks
Gurjit Bains

---

### Post by mstlyevil on 2006-04-01
[QUOTE=gurjit]I am using the account that i used to install Ubuntu with? If you need more info please tell me what i can do to help you.

Thanks
Gurjit Bains[/QUOTE]

How did you activate the root account?

---

### Post by gurjit on 2006-04-01
OK this is exactly what i do:

1. Go to Applications > Accesories > Terminal
2. cd Desktop
3. fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin

And then i get thsi error:

> gurjit@UBUNTU:~/Desktop$ fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin
You are real root -- unfortunately, some Java distributions have
install scripts that directly manipulate /etc, and may cause some
inconsistencies on your system. Instead, you should become a
non-root user and run:

fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin

which will allow no damage to be done to your system files and
still permit the Java distribution to successfully extract.

Aborting.
gurjit@UBUNTU:~/Desktop$


And thats all i do.

I hope with helped you figure out my problem.

Thanks
Gurjit

---

### Post by gurjit on 2006-04-01
Im not to sure how i activated my root user account, if i did, i dont know that i did it. Is there a way to go back to being a normal user?

Thanks
Gurjit

---

### Post by Sethiano on 2006-04-01
Hi!

I had the exact same problem as you!

My walkaround was this:

- Create a new useraccount.
- On the tab "Advanced" choose "Desktop" as the type of profile.
- Log off and log in as your newly created user.
- Start a terminal 
- (Now you can fakeroot) Create the debs with the new useraccont
- Log off and log in with your ordinary useraccont
- Install the java debs

Good luck!

---

### Post by gurjit on 2006-04-01
I tried what you said Sethiano but it didnt work. It still gives me the same error. Could it be that i selected a weird option when i installed Ubuntu that is messing this all up.

But dont worry guys, my friend did this for me on his computer and sent me the file that is created after you complete the commands that are messing me up. However i would still like to get to the bottom of this.

Thanks Alot For Your Replies.
Gurjit

---

### Post by severvip on 2008-05-21
I'm having trouble install Java to Ubuntu, I view this forum thread because I was having the same problem then I realized I was logged in as root. So I logged out as root but I'm still having a problem.


[COLOR="Gray"]user@my-laptop:~$ cd /home/user[/COLOR]

To get myself into my user folder because that is where I have the Java rpm.bin file. Nothing seems to happen when I type that though. I still get this.

[COLOR="Gray"]user@my-laptop:~$[/COLOR]

I guess I'm going to assume I'm in my user folder, even though it doesn't say. 
[COLOR="Gray"]
user@my-laptop:/home/user#[/COLOR]

Okay so now I type the fakeroot stuff and this is what appears.

[COLOR="Gray"]user@my-laptop:~$ fakeroot make-jpkg jre-6u6-linux-i586-rpm.bin
Creating temporary directory: /tmp/make-jpkg.yaEGvC9436
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

Detected Debian build architecture: i386
Detected Debian GNU type: i486-linux-gnu

No matching plugin was found.
Removing temporary directory: done[/COLOR]

What am I doing wrong, I can't figure it out. Any help is much appreciated, please I need Java, so I can install a java bittorrent client.

Severvip

---

