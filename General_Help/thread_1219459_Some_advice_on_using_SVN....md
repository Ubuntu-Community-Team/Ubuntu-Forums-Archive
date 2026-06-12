---
title: "Some advice on using SVN...?"
date: 2009-07-21
forum: General Help
---

### Post by blackandwhitepandabear on 2009-07-21
Dear list, 

I am wondering a few things about SVN. I have mostly followed
instructions for the community documentation on installation and use:
[https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion)
and also this helpful website:
[http://www.automaticable.com/2008-06-25/how-to-host-a-subversion-repository-in-ubuntu-hardy/](http://www.automaticable.com/2008-06-25/how-to-host-a-subversion-repository-in-ubuntu-hardy/)

So I have several questions regarding project creation and
distribution. 

1) Creating a new svn project. Currently for each new project I do
something like

$ sudo mkdir /home/svn/myproject
$ sudo chown -R subversion myproject
$ sudo chmod -R g+rws myproject
$ sudo svnadmin create /home/svn/myproject
$ cd ~/svn
$ svn co file:///home/svn/myproject myproject
$ mkdir myproject/trunk
$ svn add trunk
$ svn commit -m "added trunk"
$ cd ~/Document/myprojectinprogress/
$ svn import file:///home/svn/myproject

Is this about how it works? It seems a bit unnatural that I move back and
forth between the /home/svn and my local directories (~/) to do things...

2) Access for myself:

I have tried running 
$ svnserve -d -r /home/svn
(and opened up port 3690) and 'ps aux | grep svnserve' shows the server to be
running, but  
$ svn co svn://hostname/myproject myproject --username user_name
times out. My server is on an academic network with some very tough
restrictions - could that be it? I do have my Ubuntu machine running
as an SSH server, so even if svnserve is not running, I can get the files with
$ svn co svn+ssh://hostname/home/svnmyproject myproject --username
user_name
(which surprised me) I have passwordless SSH setup between my (Mac)
laptop and my Ubuntu desktop, so the SSH connection shouldn't prompt
me for a password (and it doesn't). But it also surprises me that the
svn side doesn't prompt me for anything because for each of my
conf/svnserve.conf files I have set 
password-db = /home/svn/mypasswd
and in this 'mypasswd' file I have 
myusername = mysercretpassword
set... so should not 'mysecretpassword' be prompted of me?

3) Access for others:

I'd like to share these programs I've written with my
colleagues. Should I create usernames for them on my machine and add
them to the group 'subversion' to which I have given ownership of the
project directories? I've read that I can create users who cannot log
in directly:
"Now make it impossible for anyone to log in as this user by editing
/etc/passwd to set the svn user shell to /bin/false" -http://www.subversionary.org/howto/setting-up-a-subversion-server-on-ubuntu-gutsy-gibbon-server

Since it is my understanding that all of my files in ~/ can be viewed
by other users otherwise (which is undesirable), I would like to limit
their access to just the files in the repository. Also, even if I add
their names to subversion, they would have the ability to "commit"
changes to this repository? (From the line above)
$ sudo chmod -R g+rws myproject
How can I differentiate myself (the developer) from the users of the
programs?

And is http:// access preferred over svn:// for any reason? I am not
particularly keen on setting my machine up as a webserver if svnserve
will be adequate for sharing these files...

Thanks for your time! I would appreciate any of your advice - 

Stephen

---

