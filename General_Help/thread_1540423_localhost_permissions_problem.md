---
title: "localhost permissions problem"
date: 2010-07-27
forum: General Help
---

### Post by No User Name on 2010-07-27
I have installed apache2,mysql,php .. they work great! but I can move,change,paste or anything in the folder sites_available (the folder for localhost) I am really confused right now! because I have used this with xampp in XP and it worked perfectly but I cant make it work in ubuntu! I cant test my php sites! I am really noob about configuring linux! I think I dont have permission to do anything in that folder because when I try to paste my site there it show a error saying that I am not the owner!!! when I installed ubuntu first I created a username: "SHPETIM" and this username is administrator and has root permissions but sometimes there are somethings that I cant do! sometimes even in Terminal when I type in my password (the only password that I created when I installed ubuntu) it says FAILURE! I dont know what other password it may have that I dont know! I think there is a user with username ROOT and it has another password but since I am noob I dont understand this and I dont know how it works! anybody can help me?

---

### Post by arrrghhh on 2010-07-27
Ubuntu doesn't really use a 'root' account...

Try submitting your request with 'sudo' in front.  This stands for "super user do" - basically submits the command with super-user privileges.

---

### Post by No User Name on 2010-07-27
> **arrrghhh said:**
> Ubuntu doesn't really use a 'root' account...

Try submitting your request with 'sudo' in front.  This stands for "super user do" - basically submits the command with super-user privileges.

hmmm... I dont understand why I dont have permissions in that folder! I have created that folder with this username and now it says I am not the owner! the username I am using always is the only user this PC has!

---

### Post by arrrghhh on 2010-07-27
That folder, sites_available, cannot be owned by your user.  There is a lot of sections of the Linux file system that cannot be owned by the user - this is for security reasons mainly, but having the incorrect permissions can also screw up execution of programs/services.

For example, the entire /etc section should not be owned by your user.  Technically, your user should only own their home directory.

---

### Post by No User Name on 2010-07-27
> **arrrghhh said:**
> That folder, sites_available, cannot be owned by your user.  There is a lot of sections of the Linux file system that cannot be owned by the user - this is for security reasons mainly, but having the incorrect permissions can also screw up execution of programs/services.

For example, the entire /etc section should not be owned by your user.

Have you ever had experience with LAMPP before? do you know how can I somehow chmod through terminal that folder or the complete folder of apache2?

---

### Post by OnlineBuddy on 2010-07-27
> **No User Name said:**
> hmmm... I dont understand why I dont have permissions in that folder! I have created that folder with this username and now it says I am not the owner! the username I am using always is the only user this PC has!
.
hey..i have also used apache tomcat to host applications....
.
when i used it in windows it worked fine because once you login into windows you have all powers..
.
not with linux....you will not have the power to edit that folder **$CATALINA_HOME/webapps/** where you put your application....
.
**SOLUTIONS-** 
-use terminal to do everything, type sudo before (cp - copy, mkdir - create folder) and work it out somehow!!!
-login as root, and change the permissions, i wouldn't recomment it in production environments!!

---

### Post by arrrghhh on 2010-07-27
Woah!  Did you not read what I said!??!  Both of you guys are wrong!  You CAN'T change the permissions of those files without screwing up how they work!!!!  If you do change those permissions your software **will** have issues running!

Yes, I have a LAMP stack setup on my server.  You shouldn't *need* to chmod anything in the /etc/apache2 folder.  Just edit the files with a preceding "sudo" or if you're using a gui, "gksudo".

Can you explain what the problem is?  What are you trying to achieve?

---

