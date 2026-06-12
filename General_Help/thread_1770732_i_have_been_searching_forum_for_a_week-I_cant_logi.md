---
title: "i have been searching forum for a week-I cant login"
date: 2011-05-29
forum: General Help
---

### Post by toussaint on 2011-05-29
Firstly I have searched the forum for days and tried several of the  possible solutions to no avail and so now I am asking for any assistance  you might be able to give.  

I installed Ubuntu some time ago currently using 10.10,  user name  user1, for myself and my partner (user2) and this worked fine.  My  partner has been the sole user of this machine for some time and when I  tried to log on recently I got the errors below in sequence followed by a  blank screen which would not budge until re-starting the machine.

ERRORS:
[INDENT]Could not update ICEauthority file/home/user1/.ICEauthority
[/INDENT] [INDENT]There is a problem with the configuration server (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)
[/INDENT] [INDENT]Nautilus could not create the following required  folders:/home/user1/Desktop,/home/user1/.nautilus
[/INDENT] [INDENT]Before running Nautilus please create these folders or set permissions such that Nautilus can create them
[/INDENT]  
I tried this which did not resolve the problem:
[INDENT]sudo chown -R user1:user1/home/user1/.*
[/INDENT] as well as 
 [INDENT]sudo chown -R user1:user1/home/user1/.ICEauthority
[/INDENT] and many variants of this.

Then, following some forum advice I ran this command:

user2@user1-desktop:~$ ls -l /home/user1/.ICEauthority
ls: cannot access /home/user1/.ICEauthority: Permission denied
user2@user1-desktop:~$ ls -l /home/jasmine/.ICEauthority
-rw------- 1 user2 user2 27224 2011-05-27 21:54 /home/user2/.ICEauthority
user2@user1-desktop:~$ 
 
what other info can i provide you with to help you help me

---

### Post by Ceiber Boy on 2011-05-29
When you installed ubuntu did you select the option to encrypt your home directory?

---

### Post by toussaint on 2011-05-29
I am not certain. if ithelps when i try to look at my home directory from the account of my partner i the folder has an x in the top right corner

---

### Post by lemonchicken on 2011-05-29
try booting into recovery mode and fixing broken packages. haven't had much luck with it myself but maybe it will work for yo9u..

---

### Post by toussaint on 2011-05-29
lemonchicken, have you had a similar problem?

---

### Post by lemonchicken on 2011-05-29
nope, but something is broken and fixing that will restore access to your machine.

I would, if possible
> There is a problem with the configuration server (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)remove/reinstall libconf. [probably critical]
> Nautilus could not create the following required  folders:/home/user1/Desktop,/home/user1/.nautilusuninstall Nautilus
> Could not update ICEauthority file/home/user1/.ICEauthoritydelete this file

could break it even more, so be careful :D

---

### Post by hihihi100 on 2011-05-29
Hi there: I have exactly this isssue: you may want to read: [http://ubuntuforums.org/showthread.php?p=10877766#post10877766](http://ubuntuforums.org/showthread.php?p=10877766#post10877766)
 
please read my last posts, and tell me if you also have those issues:
 
As of now Im in ubuntu IRC, I advise you to log in, my current username is Usuario

---

### Post by toussaint on 2011-05-29
Thanks lemonchicken, im not sure i will take that route. i have been investigating this issue for over a week now and there are some common solutions (which admittedly havent worked for me) I think i just need someone to guide help me find the solution that will work for me.

I have photos of my kids in my home file so cant take any unecessary risks. 
I do have acces to the machine via my partners logonbut cannot acces my home file because it is restricted. If i could get access to that file to copy its contents i would just do a fresh install

Any other suggestions out there

---

### Post by wojox on 2011-05-29
When you tried to chown there is no space between user1 and /home.

---

### Post by toussaint on 2011-05-29
Thanks for replying wojox
i tried different ways chown to make sure spacing was not an issue. In fact i  'did' chown from may partners account using her user name and that resulted in getting the ICEauthority error on her account too so change it back. I dont remember exactly what the response was when i did chown on my username but could follow any instruction you give me to get you the info you need to help me

---

### Post by toussaint on 2011-05-29
I have just done chown and recieved this response
chown: cannot access `/home/user1/.ICEauthority': No such file or directory

---

### Post by lemonchicken on 2011-05-29
sudo chown?

---

### Post by toussaint on 2011-05-29
yes sudo chown

---

### Post by wojox on 2011-05-29
Is /home encrypted?

---

### Post by lemonchicken on 2011-05-29
try creating a blank file with that name in the user1 directory

---

### Post by toussaint on 2011-05-29
How can i tell if home is incripted? I have just opened home and checked properties of user1 and in is "unreadable"

---

### Post by toussaint on 2011-05-29
The owner of "home" is root the owner of "user1" is user1-User1 (the uppercase on second username is deliberate. The owner of my partners account is user2-user2.

This seems meaningful to me(in my ignorance) because my partner is the owner of her file and can access it while i am not and cannot access it. Is thaat uppercase thing meaningful-because user 2 are both in lowercase

---

### Post by crispy_420 on 2011-05-29
Does user2 even have sudo or admin rights? Nobody seems to have brought that up. If they do not have those rights anything they attempt should fail. If another user that is not admin can access/change your home directory that is a whole other security issue.

Do you have/know your password? If so try to log in to user2, open a terminal session and su into your account (su user1) for these maintenance chores. Or you could even go about activating the root account to recover your important data.

Does anyone know if it would be safe to delete the offending file and try to login then? Often these files may recreate a clean copy right?

Here is a similar discussion:

[http://www.linuxquestions.org/questions/linux-desktop-74/iceauthority-error-in-ubuntu-8-10-a-681312/](http://www.linuxquestions.org/questions/linux-desktop-74/iceauthority-error-in-ubuntu-8-10-a-681312/)

---

### Post by toussaint on 2011-05-29
Thanks crispy
I just opened a terminal and did su then my username and password. Please tell me how this helps me access my file. i am afraid i am not expert. i tried to go via "places" computer to my file but it is still restricted. I guess i should be trying to access the file via terminal but dont know how.

Thanks in advance

---

### Post by toussaint on 2011-05-29
my partner says she gave herself admin rights. Is there a way i can confirm that

---

### Post by toussaint on 2011-05-29
sorry i just check she (user2) is definitely an administrator

---

### Post by lemonchicken on 2011-05-29
sudo touch /home/user1/.ICEauthority

don't type anything and save the file

---

### Post by linuxinstalledfromhdd on 2011-05-29
Who installed this Ubuntu for you? And did you select "encrypt home folder" during the installation process?

---

### Post by toussaint on 2011-05-29
Hi linuxinstalledfromhdd thanks for replying
A couple of others in this conversation have asked that question and i am not certain. I have asked how i can check this now but have no one has told me. Can you.

lemonchicken - what would that do

---

### Post by linuxinstalledfromhdd on 2011-05-29
The way you check this is asking the administrator for your system. Who installed it? Ask the adminstrator if they encrypted the home folder during installation.

---

### Post by toussaint on 2011-05-29
As i mentioned earlier i installed it and i do not remember if i incripted the home folder. how can i tell now and what bearing would this have on the solution to my problem

---

### Post by linuxinstalledfromhdd on 2011-05-29
If you do not remember, then we can't help you determine a course of action to remedy your situation.  You might as well reinstall at this point and do not enable "encrypt home folder" during the live installation process.

---

### Post by toussaint on 2011-05-29
is there a way of telling now whether i incripted or not? to be fair it was some time ago and i am far from expert. if not what would be the course of action if incripted and if not incripted

---

### Post by toussaint on 2011-05-29
linuxinstalledfromhddsuggests there is no way of telling if i incripted the home folder at installation besides remebering . Does anybody else know how i can tell id the folder is incripted

---

### Post by linuxinstalledfromhdd on 2011-05-29
Have you searched on google for a solution?

---

### Post by toussaint on 2011-05-29
linuxinstalledfromhdd i am sure youre trying to be helpful. you have been unable to answer any of my questions. i guess you have come to the limits of your knowledge so you can just bow out now.

---

### Post by linuxinstalledfromhdd on 2011-05-29
If you don't know how you installed Ubuntu yourself, how do you expect others to help you? Okay, let's bump this thread and see if anyone here is psychic.

BUMP

---

### Post by wojox on 2011-05-29
> **toussaint said:**
> linuxinstalledfromhddsuggests there is no way of telling if i incripted the home folder at installation besides remebering . Does anybody else know how i can tell id the folder is incripted

Boot off the live cd and mount the Ubuntu partition and try to access /home.

---

### Post by toussaint on 2011-05-29
[linuxinstalledfromhdd]("http://ubuntuforums.org/member.php?u=1050936") how about a straight answer to a straight question. Can you tell if a file is incripted because (forgive my crimes) i dont remember if i incripted them when i installed. I am happy to admit i am no expert and am simply looking for help.
You may not be psychic, but i know you can read so please read forum rules about abusive posts

---

### Post by linuxinstalledfromhdd on 2011-05-29
there is no way I can find that out by myself..

Boot off the live cd and mount the Ubuntu partition and try to access /home.

---

### Post by crispy_420 on 2011-05-30
A simple way to check encryption would be to use terminal from other user:

su user1
cd /home/user1/
ls

Kept it real simple here. You change users then navigate to home directory. Then list files.

Do you see anything familiar? Specific folders listed (Desktop, Documents, etc.)?

---

### Post by crispy_420 on 2011-05-30
Found this post in archived forums:

[http://ubuntuforums.org/archive/index.php/t-1583.html](http://ubuntuforums.org/archive/index.php/t-1583.html)

So I guess you could do this:

sudo chown user1 /home/user1/.ICEauthority

If your user2 has admin rights that should work.

---

