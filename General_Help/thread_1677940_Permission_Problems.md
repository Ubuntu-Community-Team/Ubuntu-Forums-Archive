---
title: "Permission Problems"
date: 2011-01-29
forum: General Help
---

### Post by Austin Presley on 2011-01-29
Dear All, 

  Hello everyone, I am here with a troublesome question about my new Ubuntu set up. Well as I've found out that you have to use the Sudo command to edit anything out side the home directory. Well I am using L.A.M.P. Server on my computer so I can host a small forums. Well for example like lets say I install Word press Blog onto my lamp server and I want to install a theme well when i go to install a theme i can not because WPB can't install the theme because of the security stuff on Ubuntu! 

Well I want to know if there is some kind of command or program i can use that will get rid of all the security stuff were i can edit stuff nice and easy.

Like something that can give me FULL control over the OS so no more commands because I am going to be running a Vbulliten forums which needs themes and plug ins, well i want be able to install them because this OS will not let me!

-Austin

---

### Post by InspiredIndividual on 2011-01-29
First of all, as long as you know the root password, you do have full control over your OS. It is inadvisable to disable the root password for your user account, since this is a security risk.

That being said, the problems you encounter may be caused by the fact that your user account is not the owner of the wordpress folder. You could check this by opening a terminal and executing the following command in the directory containing the wordpress folder:
```
ls -al
``` 
Your output should contain a line like this: 
```
drwxr-xr-x 5 USER USER 4096 2010-06-17 17:05 wordpress
``` 
where USER is your username. If instead it looks like this:
```
drwxr-xr-x 5 root root 4096 2010-06-17 17:05 wordpress
```
this means you don't have ownership of the wordpress folder, which might cause a problem with installing themes as you describe.

To fix this, enter the following in the terminal:

```
sudo chown -R USER:users wordpress
```
where USER is your username. Now, the wordpress folder should have the right permissions for you to change things.

Source: [http://www.ubuntugeek.com/installing-wordpress-3-0-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/installing-wordpress-3-0-on-ubuntu-10-04-lucid-lynx.html)

---

### Post by Austin Presley on 2011-01-31
Hello would i need to do this to all folders such as my forums and blog 

and also the folder that my WPB is in is called Blog, will i need to change the commands any

---

### Post by InspiredIndividual on 2011-02-01
I do not use Wordpress myself, so I am not completely sure. I suspect that all files necessary for your blog are contained in the Wordpress folder or its subfolders. This assumption is based on installation instructions for Wordpress in the article I linked to, which I surmised to be the most common setup.

The option -R in the command I mentioned means that the correct permissions are set recursively. That is, the folder itself and all its subfolders. Hence, you probably do not need to execute the command in all folders seperately (which would be very tedious, pfff...).

---

### Post by sandyeggoboy on 2011-02-02
Hi there, i am also have the exact same problems. 

Usually when i install wordpress in the past, i install it into my home dir, (/home/user/public_html/wordpress) and then create a symlink to point it to /var/www. 

Since this is a "virgin" machine, i expected no problems. but righht from the get-go i could not even browse any directory under /var/www with a browser. i keep getting a "you are forbidden to browse this folder" or something to that effect. At one point i actually thought I had it installed, and running great but that was short-lived when i realized i could not get Wp to upload any new theme files or plugins.

In the past it has always worked right out of the box. I dont know what has changed in 10.10 but i have spent all night changing permissions on folders and stuff and i am getting nowhere. I have added myself to the www-data group, the sudo group, the dammitmakethiswork group, etc .... and nothing seem to help. 

I remember however when i first installed the OS i set my home dir to private or something like that ... would that have anything to do with this problem?

---

### Post by 3rdalbum on 2011-02-02
I think you're probably going about this the wrong way. Your web server is running as a very limited user account, attempting to read the Wordpress files that are sitting in another user account (yours).

On Linux, users cannot read eachother's files, which accounts for the error message. Changing your own user's permissions won't help, because the web server's account is lacking permissions (by design, too).

I'm not sure how to achieve what you really want to do. You could install Wordpress into a root-owned location as the instructions probably tell you to do, which I imagine will set things up the way they should be. Otherwise, you could add the "Read-Only" permission for "Everybody/Others" to your Wordpress folder, and do it recursively.

From your description, you've probably already tried this, but I thought I'd suggest it just in case.

---

### Post by InspiredIndividual on 2011-02-02
> **3rdalbum said:**
> I think you're probably going about this the wrong way.

Possibly... After all, the Ubuntugeek article I mentioned was about installing Wordpress on Ubuntu 10.04. As sandyeggoboy had no problems before, this might be a Ubuntu 10.10 specific issue. I have no clue about what difference between 10.04 and 10.10 could cause this, unfortunately.

---

