---
title: "NOOB question: How do I create folders in the file system?"
date: 2010-10-15
forum: General Help
---

### Post by razorneck on 2010-10-15
Why am I trying to create folders in the file system you ask? I'm messing around with Drupal and I want to add some modules. So I need to go to the blablabla/sites/ folder and add an 'all' folder followed by a 'modules' folder.

No problem, right? Wrong?

It seems I don't have the rights to create folders in the file system ( which I only recently figured out is actually root. duh. )

I've figured out that I was able to install all the LAMP parts because I was using 'sudo' before every command, which apparently grants me temporary rights to root? ( I think? )

Sooo... what's the magic for creating folders and transferring files to my Drupal folder... which it seems requires root permissions?

...

... told ya I was a noob. #-o

( please use small words. My brain already feels like it's leaking out my nose. )

---

### Post by ron999 on 2010-10-15
Hi
If your file manager is Nautilus use command:-
```
sudo nautilus
```

---

### Post by ragtag on 2010-10-15
Let's just start with the basics. I'm assuming you're doing this on the command line, so you'll need a couple of basic commands to move around.

To open a folder
cd foldername

To go up one folder
cd ..

To see what's in the folder, with permissions and details (the "a" shows hidden files too).
ls -la

To make a folder
mkdir folderName

To make a folder as root (where you don't have permissions to)
sudo mkdir folderName

To copy files from one place to another.
cp sourceFile destionationFile
cp myFile /tmp/myFile
 (this is the same as)
cp myFile /tmp/.

To copy whole folders use
cp -R source destination

And like with mkdir, you can simply add sudo in front to copy with root privileges.

Finally, you can run nautilus the file manager as root, by typing (though it's probably not recommended).
sudo nautilus --no-desktop

Three last commands you should know.
man <- This, followed by any command shows you the manual for that command.
chmod <- This changes the permissions of files and folders. Run "man chmod" for details.
chown <- Changes the ownership of files and folders. Again, you can run "man chown" for details.

You might want to check if the modules you need are available through apt-get (or Ubuntu Software Center or Synaptic Package Manager if you prefer). This will make installing them much easier.

---

### Post by razorneck on 2010-10-15
Well that's very informative, thank you!

I was kind of hoping I could just enable read/write permissions for the drupal folders so I could just drag stuff into them all windows-like. Is that a possibility? I'm really slow at the command line stuff still...

---

### Post by ragtag on 2010-10-16
The best way to do this is probably to just take ownership of all the drupal files and folder, and then change the web server to run as you (I'm assuming here this is just a test install you're using for development, and not a live server on the net).

To take ownership of all the drupal folders, use the following command.

```
chown -R you.you yourDrupalFolder
```

Replace you.you with your username twice (the second is actually the group name, but it's generally the same). And the yourDrupalFolder with the path to the Drupal folder.

This means you can use the normal file browser, gedit or whatever, without sudo, to edit, copy, delete etc. files within the drupal folder.

The problem with this is that your web server most likely doesn't run as you, it runs as either the www-data user or apache user. So the web server may not be able to read all the files, and Drupal will fail. To fix this you can run Apache2 (the web server) as you. To do this you need to edit the file.

```

/etc/apache2/envvars
```

You can open it by typing

```
sudo gedit /etc/apache2/envvars
```

Change these two lines:

```
export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data
```

Just replace the www-data user, with you username. Then you need to restart apache, by typing:

```
sudo service apache2 restart
```

Hope that helps. :)

---

### Post by Dans564 on 2010-10-16
you could also just run
```
sudo nautilus
```
as said above.  This will allow you to move folders and such with a window and virtually no command line, except of course "sudo nautilus"

---

### Post by yetiman64 on 2010-10-16
@ragtag and ron999 and Dans564,
Please note using "sudo" with graphical apps is potentially damaging to a users system, "**gksudo**" should be used instead for gedit and particulary for nautilus.

The section "Graphical Sudo" in  Link #4 in my sig has an explanation as to why.

More info on the subject is at [--Psychocats.net--]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by Dans564 on 2010-10-16
wow i did not know that:shock:
yea take his advice lol

---

### Post by ron999 on 2010-10-16
@yetiman64
It's a pity that you weren't available to answer the OP's question.

---

### Post by CharlesA on 2010-10-16
> **ron999 said:**
> @yetiman64
It's a pity that you weren't available to answer the OP's question.

No need to be rude.

See [here]("https://help.ubuntu.com/community/RootSudo#Graphical%20sudo") as to why you use gksudo or kdesudo instead of plain sudo for graphical apps.

---

### Post by dcstar on 2010-10-16
> **ragtag said:**
> 
........
Finally, you can run nautilus the file manager as root, by typing (though it's probably not recommended).
sudo nautilus --no-desktop
........

There is **no need whatsoever to use the command line** for any of this.

Simply install the **nautilus-gksu** package and you can open any folder with root privileges, and then create/set rights to anything all using Nautilus.

It is far better for any new users to stick with a GUI tool that will do the job rather than be hit with arcane command line things that they can damage their system with if they make a typing error.

---

### Post by CharlesA on 2010-10-16
> **dcstar said:**
> There is **no need whatsoever to use the command line** for any of this.

Simply install the **nautilus-gksu** package and you can open any folder with root privileges, and then create/set rights to anything all using Nautilus.

Good point.

You can also just hit alt+F2 and type in *gksu nautilus*

:)

---

### Post by razorneck on 2010-11-05
Thanks everybody! 

Yes, I think it best that I stick to the GUI interface for now - though I do find sudo apt-get install rather addicting for some reason, hehe. Feels like I'm hacking the matrix or something :guitar:

---

