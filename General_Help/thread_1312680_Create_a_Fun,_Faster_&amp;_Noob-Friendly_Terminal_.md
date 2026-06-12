---
title: "Create a Fun, Faster &amp; Noob-Friendly Terminal .. YES, FOR REAL!!"
date: 2009-11-03
forum: General Help
---

### Post by the_guv on 2009-11-03
[SIZE=3][COLOR=Sienna]Here's Part 7 from ..[/COLOR][/SIZE][SIZE=1][COLOR=Sienna]
[/COLOR]
[/SIZE] [COLOR=MediumTurquoise][U][SIZE=4] [guvnr.com's new 25-part Karmic Koala Bible]("http://guvnr.com/pc/karmic-koala-bible")[/SIZE]
[/U][/COLOR] [SIZE=1][COLOR=Sienna]
[/COLOR][/SIZE][SIZE=3][COLOR=Sienna]Full of tips, tweaks & cheatsheets, it's ideal for beginners and intermediate users, assisting setup, enhancement & use of Ubuntu's top new edition.
[SIZE=1]
********************************************************************************
[/SIZE] [/COLOR][/SIZE][SIZE=1]
[/SIZE] [SIZE=3]This how-to - into using simple memorable  commands, not complex syntax - will make you not only faster at the  Linux shell, but enjoy it too. 
[SIZE=1]
[/SIZE] [/SIZE] [SIZE=3][COLOR=Red]Honest guv!  If you love Ubuntu but struggle with the terminal, you are gonna adore this guide.
[/COLOR][/SIZE][SIZE=1]
[/SIZE]  Copying over my old **bashrc** file to a new install (it  lives in your /home/username folder) is  the first thing I do after a new Ubuntu install because it speeds up and simplifies everything else  .. especially for someone with a memory as bad as mine. 

*So what is  bashrc?*
 
Here's the thing: such is Linux, to make the most of it, we use the  terminal a whole lot. Not that you have to - you can get away without,  but that's like drinking non-alcoholic beer.  Hic.
 
To make the command line experience way faster, less dour, more  powerful, even fun, we edit this thing called the bashrc file. 
 Open:-
 
nano ~/.bashrc

.. and prompted, give the password you created at the Ubuntu  installation stage, if any.
 Scroll to the bottom of the file and paste whatever you fancy from  below, modifying the aliases to suit you.  I've made comments beside the  "###heading" for each section to clue you in:-
[FONT=monospace]
[/FONT]########################################################################

  ###My Most Basic Aliases .. these ones are useful to everyone

#open bashrc
alias ebrc="nano ~/.bashrc"
#update .bashrc
alias ebrcupdate="source ~/.bashrc"
#open software repositories
alias repos="gksudo gedit /etc/apt/sources.list"
#update software source index
alias update="sudo aptitude update"
#Ubuntu version detail
alias ver="cat /etc/lsb-release"
#safe upgrade Linux OS
alias upgrade="sudo aptitude safe-upgrade"
#full upgrade Linux OS
alias fupgrade="sudo aptitude full-upgrade"
#install [software_name]
alias install="sudo aptitude install"
#remove [software_name]
alias remove="sudo aptitude remove"
#RAM and SWAP detail in MBs
alias free="free -m"
#detail list of current dir
alias ll="ls -lha"

###Local Web Server .. just to give you an idea of the power of bashrc (3 commands in 1 here)

#reload Nginx
alias n2r="sudo /etc/init.d/nginx stop && sleep 2 && sudo /etc/init.d/nginx start"

###Network .. this example executes a script

#mount dirs from a file server (called PETE) as selected in $Pete/etc/exports (an sh file), to /mnt/PETE/xxx
alias PETE="./PETE.sh"

###Wiki .. this one backs up a local db

#dump someDB
alias someDBdump="sudo mysqldump someDB -uroot -p > /home/username/www/_dbs/someDB.sql"

###Remote Hosts .. these play with a remote server

#access some remote host
alias remote="ssh -p 1234 12.34.56.78"
#access some folder
alias uploads="cd /some/folder"
#copy remote db to local
alias dbdumpcp="scp -P 1234 [EMAIL="username@12.34.56.78:/home/username/Backup/www/data/someSite/db.sql"]username@12.34.56.78:/home/username/Backup/www/data/someSite/db.sql[/EMAIL] /home/username/Backup/data/db.sql"

###SOCKS proxy .. these anonomise my browsing with a single word

# 12.34.56.78
alias proxy1="ssh -p 1234 -D 5678 username@12.34.56.78"
# 87.65.43.21
alias proxy2="ssh -p 8765 -D 4321 username@87.65.43.21"

###Sync to PDA .. well, that'll be a sync then!

#Start FinchSync SVR
#alias sync="java -jar /home/olly/finchsync/finchsync.jar -nogui"
#Stop FinchSync SVR
#alias syncoff="java -jar /home/olly/Apps/FinchSync/finchsync.jar -stopserver"
#Start FinchSync Admin
#alias finchsync="java -jar /home/olly/finchsync/finchsync.jar"

###My Functions .. not a command but a function. Below makes Terminal colorful. Different colors differentiate machines to help prevent errors.  Hmmn, there's only 1 here .. I should get more into functions!

#add color & formatting to CLI

export PS1="\[\e[35;1m\]\u\[\e[0m\]\[\e[32m\]@\h\[\e[32m\]\w \[\e[33m\]\$ \[\e[0m\]"

########################################################################

The way these work is pretty self-explanatory but,  to break down an example, this one is the shortcut to open this file,  bashrc, for when we want to add more cool 'cuts:-
 
alias ebrc="nano ~/.bashrc"
 
[LIST]
[*]alias ebrc tells bashrc we're issuing  an alias directive, and that the alias itself will be "ebrc" (it could  be mostly anything you like)
[*]= well, it's an equal sign, obviously!
[*]"nano ~/.bashrc" is the quoted,  properly syntaxed command we would normally provide
[/LIST]
 So, instead of issuing nano ~/.bashrc,  now all we need type is ebrc.
 
That won't work though, until we restart bashrc, by typing:-
 
source ~/.bashrc 

As you may have seen, I've even shortcut the command to restart  bashrc.  Having set an alias to restart bashrc - ebrcupdate  - and restarted bashrc one last time with it's regular restart command,  source ~/.bashrc), thereafter I type ebrcupdate.
 
You may imagine, this bash thing is darnedly handy, especially when  maneuvering about remote servers where you also have a jazzed up bashrc.  I log into the server for this site, for example, with this command:-
 
guv

And if I want to open my SOCKS proxy, depending on where I want to  pretend to be, I just type:-
 
proxyUK

.. or ..
 
proxyUS

How handy is that? Especially for a bloke like me who, like I say,  can barely remember the, er .. can't recall what I was gonna say there.

************************************************************************

Want more like this?

>>> guvnr.com

---

