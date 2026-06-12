---
title: "Samba - Make Directory"
date: 2012-04-23
forum: General Help
---

### Post by Digitalscribbler on 2012-04-23
Hi-
I've downloaded Samba and now I'm trying to create a directory via the Terminal. When I enter the command

[FONT="Courier New"]mkdir/home/camalas/test[/FONT]

I get the error 'no such file or directory'

*Important Note*: I'm using Jonathan Mueller's book Beginner Ubuntu [http://www.jonathanmoeller.com/screed/](http://www.jonathanmoeller.com/screed/) and he emphasizes NOT to use sudo to create the new directory. Any ideas on what the problem might be? Thanks!

---

### Post by papibe on 2012-04-23
Hi Digitalscribbler.

There has to be a space between the command and its argument:
```
mkdir  /home/camalas/test
```
Hope that helps, and tell us how it goes.
Regards.

---

### Post by Digitalscribbler on 2012-04-23
> **papibe said:**
> Hi Digitalscribbler.

There has to be a space between the command and its argument:
```
mkdir  /home/camalas/test
```
Hope that helps, and tell us how it goes.
Regards.

Thanks for the suggestion. I tried that, but unfortunately got the same error. 
However, I quit the terminal since last trying this mkdir command, so I wonder if I need to do something else (e.g., access samba and then enter the mkdir command?).

---

### Post by Roasted on 2012-04-24
How are you logged in? Are you remoted in from another system, or is this entirely local? I.E. are you trying to create a directory on this system from across the network?

---

### Post by papibe on 2012-04-24
A few thoughts:

If /home/calamas does not exist you can't create a directory under it, unless you use the -p option:
```
mkdir  -p  /home/camalas/test
```
That translate into first creating 'calamas' and then test. However, the creation of /home/calamas won't work without sudo, since a regular user can't create directories at that level.

Could you explain us what are you trying to do?

Regards.

---

### Post by Digitalscribbler on 2012-04-24
Sure, I'm trying to set up a Samba server to store and share files. Thanks.

Quick background notes: so I've installed Samba (e.g., sudo apt-get install samba), and set up a password (e.g., sudo smbpasswd -a camalas).

---

### Post by Morbius1 on 2012-04-24
I've read the only reference I could find in your link concerning Samba: [http://www.jonathanmoeller.com/screed/?p=3556](http://www.jonathanmoeller.com/screed/?p=3556)

> For example, to create  a command for a user named camalas, here’s how the command should look: **sudo smbpasswd -a camalas**
It's an example. You are supposed to use your own user name not camalas. If you want to use camalas then you can but then you need to follow [COLOR=Blue]**papibe**[/COLOR]'s [COLOR=Black]procedure since /home/camalas doesn't exist.[/COLOR]

---

### Post by Digitalscribbler on 2012-04-24
> **papibe said:**
> A few thoughts:

If /home/calamas does not exist you can't create a directory under it, unless you use the -p option:
```
mkdir  -p  /home/camalas/test
```
That translate into first creating 'calamas' and then test. However, the creation of /home/calamas won't work without sudo, since a regular user can't create directories at that level.

Could you explain us what are you trying to do?

Regards.

Thanks again for your feedback, but I have a question. Do you know why Mueller (the author of [this book]("http://www.amazon.com/The-Ubuntu-Beginners-Guide-ebook/dp/B004Y1NMDI/ref=cm_cr_pr_product_top")) would say not to use sudo to create this folder. I've quoted the place where he says this below in order to provide a little more context.
[INDENT][FONT="Courier New"]"(NOTE: DO NOT use sudo to create the folder, because then the owning user and group will be set as 'root' which means you won't be able to access the folder using your Samba username and password.)"[/FONT][/INDENT]

I did a little further research and found another Ubuntu forum [post]("http://ubuntuforums.org/showthread.php?p=7631542") that says I should use sudo to do the mkdir command. However, it's from back in 2009 (Hardy Heron) and so I don't know if it's still applicable; it seems like terminal commands wouldn't change too much since they're Unix-based (i think). Maybe Mueller just has an inaccurate understanding regarding this ...

---

### Post by Digitalscribbler on 2012-04-24
> **Morbius1 said:**
> 
It's an example. You are supposed to use your own user name not camalas. If you want to use camalas then you can but then you need to follow [COLOR=Blue]**papibe**[/COLOR]'s [COLOR=Black]procedure since /home/camalas doesn't exist.[/COLOR]

Thanks.

---

### Post by audiomick on 2012-04-24
I just tried this out, and found I couldn't create a directory in /home without using sudo. Surprised me, actually.

Using sudo, I got a directory that was owned by root, as I expected.

I can never remember the right numbers to use with chmod, so I always use an instance of Nautilus with root privileges for changing the permissions and ownership of files owned by root. To start such an instance of Nautilus

```
gksudo nautilus
```

In there, right click on the folder and go to the permissions tag. Change the owner and the group to you, and set the permissions as you want to have them.

If you want to look into chmod and chown, look at the man pages
```
man chmod
```
```
man chown
```

---

### Post by PinkFloyd102489 on 2012-04-24
4 = read
2 = write
1 = execute

Each permission is split into three groups. Owner, group, and all.

So if you want to give read/write access to owner and group, but only read access to all, do:

```
chmod 664 test.file
```

I don't really use chown that often but I normally use it recursively.

Example:

```
chown -hR username:group directory/
```

This will make the specified directory and all files under it owned by the user and group given in the command.

---

### Post by Morbius1 on 2012-04-25
> Do you know why Mueller (the author of [this book]("http://www.amazon.com/The-Ubuntu-Beginners-Guide-ebook/dp/B004Y1NMDI/ref=cm_cr_pr_product_top")) would say not to use sudo to create this folder.Mueller is specifically talking about creating a subdirectory in your own home folder. If you do that as sudo then the owner of the directory will be root not you.

Run the following command from the terminal:
```
ls -dl /home
```You will see that the ownership and permissions look something like this:
> drwxr-xr-x 5 root root 4096 2012-04-19 07:53 /homeRoot has read/write access and everyone else has only read access. A non root user cannot create a subdirectory off /home itself only root ( sudo ) can do that.

Now run the same command from your own home directory. If your user name is morbius for example:
```
ls -dl /home/morbius
```You will see that ownership and permissions look something like this:
> drwxr-xr-x 45 morbius morbius 4096 2012-04-25 06:01 /home/morbiusNow I'm the owner of the folder and everyone else ( except root ) can only read.

If I create a subfolder in my own directory as sudo I will not be able to have write access to the folder. If I create the subfolder without sudo I will.

---

### Post by Digitalscribbler on 2012-04-25
> **Morbius1 said:**
> Mueller is specifically talking about creating a subdirectory in your own home folder. If you do that as sudo then the owner of the directory will be root not you.

Thanks a lot! That clarified it for me.

---

