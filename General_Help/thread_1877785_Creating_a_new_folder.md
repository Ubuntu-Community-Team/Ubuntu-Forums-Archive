---
title: "Creating a new folder"
date: 2011-11-08
forum: General Help
---

### Post by glennbates on 2011-11-08
I want to create a folder in my www folder for a web site I am working on.  How do I do that?

---

### Post by lisati on 2011-11-08
Assuming you have some content somewhere, you can do something like this from the command line: ```
sudo mkdir /var/www/*{foldername}*
``` - you can then copy your content to /var/www/*{foldername}* and then access it at http://your.site.name/{foldername}

(Don't forget to replace "*{foldername}*" with the real name of the folder.)

---

### Post by mikewhatever on 2011-11-08
You should use the **mkdir <folder_name>** command, or **sudo mkdir <folder_name>** if admin privileges are required.

---

### Post by glennbates on 2011-11-08
When I try to create it with bluefish, it says 

"The folder couldnot be created"
"Error creating directory: Permission denied"


I don't like my computer telling me my permission is denied.  That's why I left Windows.  I tell it what to do, not it tells me what I can do.

---

### Post by lechien73 on 2011-11-08
It's telling you that permission is denied to stop you doing things accidentally - that an administrator would do.

If you open a terminal window and type the command lisati gave you:

```
sudo mkdir /var/www/{foldername}
```

(replacing {foldername} with the actual name of the folder) then it will be created.

The "sudo" command runs the subsequent command as an administrator, so it overrides the permissions.

You really are a lot more free to do what you want and to tweak things with Ubuntu, but it does have some protection built in to stop you doing things you might later regret :)

---

### Post by muteXe on 2011-11-08
wtf are you creating it in bluefish?
Do it from the command line.

edit: beaten to it again...

---

### Post by glennbates on 2011-11-08
> **lechien73 said:**
> It's telling you that permission is denied to stop you doing things accidentally - that an administrator would do.

If you open a terminal window and type the command lisati gave you:

```
sudo mkdir /var/www/{foldername}
```(replacing {foldername} with the actual name of the folder) then it will be created.

The "sudo" command runs the subsequent command as an administrator, so it overrides the permissions.

You really are a lot more free to do what you want and to tweak things with Ubuntu, but it does have some protection built in to stop you doing things you might later regret :)
I did that and it worked.  Thanks

My problem now is when I try to copy my contents over to it, I get:

"Error while copying."
"The folder 'includes' cannot be copied because you do not have permissions to create it in the destination."

How do I change "permissions"?

---

### Post by glennbates on 2011-11-08
Nor can I copy any of the files.  The files from my web site are on my thumb drive.  I am trying to copy them to a folder I just created in the www folder.  How do I do this?

---

### Post by muteXe on 2011-11-08
The 'problem' is that, as a normal user, you are trying to copy files to a location that you do not 'own'.  It's this kind of thing that makes linux a LOT more secure than windows.
You need to use cp to copy files from the command line, but also, as you are copying files into an area that is outside your normal user account you need to use 'sudo cp .....'.

lechien73 explained what sudo means.

edit: you could do "sudo nautilus' from the command line. This will open up your file browser with sudo privs. HOWEVER, this is quite a dangerous/silly thing to do.

---

### Post by lisati on 2011-11-08
"[sudo]("https://help.ubuntu.com/community/RootSudo")" is your friend. One of the more common uses seen in the forums is to let you *temporarily* have the necessary permissions to do stuff in system folders.

Instead of **cp {source} {destination}** you'd use **sudo cp {source} {destination}**

---

### Post by lechien73 on 2011-11-08
Is this a personal machine, or will this be where the website will actually be live?

If it's a personal machine, inside your own firewall and the apache server is not exposed to the Internet, then you can change the permissions of the folder you just created by typing:

```
sudo chmod 777 /var/www/{foldername}
```

Again, replacing {foldername} with the actual name of the folder.

You can copy the files, as has been previously mentioned by using

```
sudo cp ...
```

If you're trying to copy the files using Bluefish, then you could run Bluefish as an administrator user by typing:

```
gksu bluefish
```

But be aware that, as muteXe says, running these things as root is dangerous!

---

### Post by BillyBoa on 2011-11-08
I any case you can execute 
```
sudo nautilus
```
and create folders and copy files, but later on will have problems with permissions on the files created by admin.

---

### Post by lisati on 2011-11-08
> **BillyBoa said:**
> I any case you can execute 
```
sudo nautilus
```
and create folders and copy files, but later on will have problems with permissions on the files created by admin.

**gksudo** is usually better than sudo for graphical applications such as nautilus. Take a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by glennbates on 2011-11-08
> **muteXe said:**
> wtf are you creating it in bluefish?

erm, because I am trying to work on a web site.

---

### Post by glennbates on 2011-11-08
Well, I got everything copied and tried to open it up using firefox.  Thinking all was about to be well, I get the little box:

You have chosen to open
which is a phtml file
from [http://localhost](http://localhost)
what should firefox do with this file?
open with [Browse...]
Save file
[Cancel][ok]


What's wrong now???

---

### Post by lechien73 on 2011-11-08
You need to install PHP. From a terminal window run:

```
sudo apt-get install php5
sudo apt-get install libapache2-mod-php5
sudo /etc/init.d/apache2 restart
```

And try the page again.

---

### Post by glennbates on 2011-11-08
> **lechien73 said:**
> You need to install PHP. From a terminal window run:

```
sudo apt-get install php5
sudo apt-get install libapache2-mod-php5
sudo /etc/init.d/apache2 restart
```And try the page again.
I did install it.  When I go to the root "localhost" I get:

**It works!**

 This is the default web page for this server.
 The web server software is running but no content has been added, yet.

---

### Post by lechien73 on 2011-11-08
Ok, that shows that apache is installed. If you run:

```
php -v
```

in a terminal window, what output do you get?

---

### Post by glennbates on 2011-11-08
Ok, it's working now.  Or at least it isn't giving me the message.  I just needed to do the 
sudo /etc/init.d/apache2 restart
Now, I run my index.php file and I only get a blank screen.  When I view the source, it has nothing in it.  When I open the index file up in bluefish, I see that everything is there.

---

### Post by lechien73 on 2011-11-08
Hmmm...well, if you've confirmed that PHP is installed, by running:

```
php -v
```

And your index.php file is showing no source, then for some reason it's not producing any output.

You could try creating a test.php file consisting of:

```
<?php
echo '<HTML><BODY>test</BODY></HTML>';
?>
```

and see if that works. If so, PHP is running correctly and the issue lies in your index.php file, which is beyond the scope of this forum.

---

### Post by glennbates on 2011-11-08
Something must be wrong with my include statement.  It works on my server but not on my local host.

Here's the code:

```

<?php
$title="Study Question | Your Study Buddy";
$currentpage="includes/pages/index.php";

include "includes/page.php";

?>

```

---

### Post by lechien73 on 2011-11-08
The include file is probably missing. The page.php file is in a directory named includes, which should be in the same directory as the index.php file. If you look on your server you will probably have the includes directory. This also needs to be copied to your var/www/{foldername} directory in order to work.

It sounds like you're most of the way there, just a few missing files and you should be done.

I'm going to bed now, so hope you get it sorted. If not, we can pick it up tomorrow :)

---

### Post by glennbates on 2011-11-08
The file is there and in the includes folder.  I have it opened up in bluefish also.  Not sure why it's not "including" it.

---

### Post by glennbates on 2011-11-16
> **lechien73 said:**
> Is this a personal machine, or will this be where the website will actually be live?

If it's a personal machine, inside your own firewall and the apache server is not exposed to the Internet, then you can change the permissions of the folder you just created by typing:

```
sudo chmod 777 /var/www/{foldername}
```Again, replacing {foldername} with the actual name of the folder.


How do I include all higher lever folders within this folder.  For example, when I give this 777 privilege, it does not allow privilege for the img folder.

---

