---
title: "LDAP? SSH? How to logon to network?"
date: 2006-04-08
forum: General Help
---

### Post by zx2c4 on 2006-04-08
My school uses Macs. They run Mac OS X Server. At each computer in the computer lab, each student is able to logon using their username and password to their "own desktop" because each computer is authenticated remotely and their home folder is a remote mount. All programs run locally. 

At studentserver.myschool.org, they run an appletalk file share server, perhaps another sort of file sharing server, and an ssh server, all of which I can logon to using my username. At queenbee.myschool.org, the school runs an ldap server which is used for authentication on each of the computer lab computers. Logged in as administrator, I looked at the directory services program to obtain ldap information. They connect to the queenbee server and use the base of dn=..... Also part of this string is cn=config and it is setup to get all details "from server". All user name entries have the normal objectType=posixAccount in addition to some unique apple attributes.

One of the attributes is homeFolder. For me, this is located at /Network/studentserver.myschool.org/Volumes/Hive/myUserName. Logged onto my account using a mac, in addition to my home folder being present as I have all my settings unique to me, I can type cd ~ in terminal and get my homefolder, which is mapped to this path. I can also cd /Network/studentserver.myschool.org and peak around. My authentication to this server is based on my username and the group that I'm in (which was authenticated by ldap before), so it is safe to conclude that studentserver.myschool.org also logs into this ldap server and authenticates me using normal credentials.

I installed Linux on one of the G5 towers. How can I set the computer up such that users are able to login to it using their username and password and have their home folder be their server share?  OpenLDAP? SSH? AFP? I have tried openldap and I have been unable to get that to work (ldapsearch -x 'uid=myusername' works but I can't get system wide authentication working).

If I did get OpenLDAP to work, what about the home folder? The homeFolder attribute ldap mentions refers to a specific place already existant on the mac computer (/Networks/studentserver.myschool.org), so perhaps the equivalant would be to have /Networks/studentserver.myschool.org in /etc/fstab and mounted.

The next question, however, is how can I have this mount like a normal device directory which uses normal authentication? I have tried specifying nfs as a fs type, but this does not work. Perhaps I can utilize the existance of an ssh server running? What about afp? But then I have to be careful that it uses the normal system wide authentication mechanism (that authenicates my access to local folders, for instance) and not a logon of its own.

And on top of that, even after getting OpenLDAP to authenticate system wide, how will it know to make the homefolder based on the homeFolder attribute?

Or perhaps there's another way to do this, completely through ssh, but that's doubtful. Any ideas?

---

### Post by Achille on 2006-04-11
On the Ubuntu client, you have to install the packages libnss-ldap and
libpam-ldap. Then open a terminal as root (and leave it open, because a
bad operation could make impossible to login anymore).

Replace the files 

/etc/nsswitch.conf
/etc/pam.d/common-account
/etc/pam.d/common-auth

with those that I send you (copy the original files before so that you
can restore them with the first root console, if you have a problem!)

It should then be possible to login. Test it: open a third console as
root and type

login

and test with a ldap user.

If it works, login as ldap user with gdm. You will get an error message
about the home directory. You have to note the path of the home
directory.

On the Mac OS X Server, enable the nfs export for the home directory.
And on the Ubuntu client, modify the file /etc/fstab and add such a
line:

192.168.2.6:/Volumes/Repertoires /Network/Servers/XServeMaitreCham/Volumes/Repertoires nfs rw,rsize=8192,wsize=8192 0 0

You have, of course, to adapt the ip adress and path to your
configuration. Create the folder on the Ubuntu client according to this
path and mount the home directory with the command: sudo mount -a

Finally, if "john" is the name of a local user of the Ubuntu client with
all the rights you want (access to cdrom and so on), type in a terminal:

id john

to get all the groups he belongs. On the Mac OS X Server, you have to
create new groups with the same GID (Group Identification Number) and to
add all the users in these groups.

I hope it will help you. Ask me again if you have some difficulty.

Now my question: it is very difficult to convince the computer's
responsable of my school to install Ubuntu for the students (I did it
only for the teachers). Has your school Macintosh computer with MacOSX?
Why do you migrate to Linux? What are the reasons? Please let me know
what happens in your school.

---

### Post by jockeschmidt on 2006-06-13
Im about to try the same setup. All OSX, network home on OSXserver.

I want to get some Ubuntu clients running for different reasons, show the students what it looks like, theyve never seen linux. And I want to be in a Linux-world in some future... spread the knowledge and educate myself mainly.

But this hack is not easy. Hopefully someone with skill will make a "Connect Linuxclient to OSX server with home"-hack.

/Jocke

---

