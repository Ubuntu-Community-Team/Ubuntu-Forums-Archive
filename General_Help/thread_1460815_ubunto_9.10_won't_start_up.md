---
title: "ubunto 9.10 won't start up"
date: 2010-04-23
forum: General Help
---

### Post by ashen02 on 2010-04-23
im a beginer in ubunto after installing the new version of miro and adding a new resource list with miro synaptic install python  and now my ubunto won't start up  when i did boot in recovery mode and try the gpk repair it showed that the line 57 in etc/apt/resources.list is broken when i boot in normal mode it appears a loging screen when i enter the user pass correctly  its reappear again plz help it took me 10 days to finally set my ubunto to work fine and now it can't boot plz help

---

### Post by klemes on 2010-04-23
Look do not panic stuff like this is happening all the time.At the worst case scenario you will simply have to reinstall....:)

But tell me are you able to login as root or as another user????
Or can you login pressing Ctrl+Alt+F2 and giving your username and password there???

If so it would be good to type:

 ls -al
 

and make sure that every single file with a dot (.)in front of it's name is owned by your user.

also look at your ~/.profile for any invalid paths and last

take a look at your /var/log/Xorg.0.log and /var/log/messages logs for any error meessages.:popcorn:

---

### Post by ashen02 on 2010-04-23
ok i can log as root

---

### Post by klemes on 2010-04-23
That's vaery good.Are you logged-in in a graphical environment(gnome?) or in a terminal?
:guitar:

---

### Post by ashen02 on 2010-04-23
i logged in terminal
and the ls -al cmmand worked an all the .* are owned by me 
but as you know im a newbe in ubunto i couldn't use the other command

---

### Post by klemes on 2010-04-23
Still logged in as a root in a terminal?
Tried to log in as your user(ie with your username)in another terminal to see if it is possible?
Pease try and tell us.
And last are you able to get into a graphic environment (Gnome) even as root ,because that would simplify things a lot....
And it would help to know how are you typing these posts so as to know if you are able to copy & paste things from your screen or not. Do you use another computer from the one you are trying to fix to post here?
:popcorn:

---

### Post by ashen02 on 2010-04-23
yes i can log in with my username

when i start up in normal mode it appears a log in screen  in graphic but it wont log in it reapear all the tivie
 
i m typing these replys in windows wich is too installed in my machine

---

### Post by klemes on 2010-04-23
So you are writing these from a  windows installation from the same machine .This means no easy way to paste text here.Look I have no easy answers on this but let's summarize :You are able to login as a root and as user in a terminal but you are unable to login as user into graphic environment.I am assuming that you are able to login as root into Gnome as root (correct me if I am wrong)meaning that your xserver installation is intact and the problem resides only somewhere in your home directory.
Now if I were you I would login in a terminal as user
and first look at my ~/.bashrc and my ~/.profile and check that everything is OK there and that there are no invalid PATHS there,since you have said that you have installed some programs before this anomaly occurred.
Also try to have a look in the your ~/.xsession-errors and also into your /var/log directory especially the gdm subdirectory for errors.Keep looking and you will find the culrpit.
If you find something and you want to show us in order to help correcting it you must manually mount the windows parttion ,ie:
sudo mkdir /media/windows && sudo mount -t ntfs /dev/sda1 /media/windows
(note I am assumnig that you have windows in your first parttion of your first HDD here.If not adjust /dev/sdXX accordingly)
and manually copy the log file there (eg cp 'name of logfile' /media/windows) so as to have it available in your root partition (C:\ drive in windows)when you reboot into windows again.
Also you could try to make another user temporarily with the adduser command(sudo first)so as to be able to use the graphic environment logged-in as taht user and not to be obliged to reboot into windows every now and then.

---

### Post by ashen02 on 2010-04-23
i add new user but same thing it showed a logi in screen with the two users  but an error appears it said gnom energy some thing... is broken contact your service ....

---

