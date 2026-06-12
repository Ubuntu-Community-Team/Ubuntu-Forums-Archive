---
title: "New to linux, ftp server is the goal"
date: 2006-05-06
forum: General Help
---

### Post by Cellwind929 on 2006-05-06
I have played with kubuntu and a slax live cd before. I am slowly learning about linux.

Right now I will be installing Ubuntu 5.10 onto my secondary computer. (right now I'm having install issues, probably a bad cd)

Once I get ubuntu up and running. I would like to be able to set up an ftp server. I would like to host videos I have made. I just want people to be able to download and upload files. The question I have is this: which program/setup should I use to get this idea off of the ground?

I would prefer a GUI based FTP program due to me coming from windows and still learning the command prompt/terminal commands (intimidating as they may be).

Links to guides, posts, or sites with info would be wonderful. Thank you all in advance.

---

### Post by rvergara on 2006-05-06
Welcome to Linux/Ubuntu.

I personally use vsftp (it stands for very safe ftp)

Just open synaptic (->system->administration->synaptic) and search for vsftpd and install it.

That is it!

By default it creates a public ftp site in /home/ftp

To browse to this site just type ```
gksudo nautilus
``` You can also create a launcher on your desktop with this command so you do not have to enter it in a terminal.

To make available files in your public ftp just copy the target file and paste it in your /home/ftp folder using nautilus. It can not be easier that that.

If you need autheticated user accounts in your ftp, just create a new user in ubuntu (->system->administration->users), create the username and password and you have a new ftp account. You can make file availables for that ftp account dropping target files in /home/<newusername>

Regards

Ramiro

---

### Post by z_diver on 2006-05-06
[quote=rvergara]
If you need autheticated user accounts in your ftp, just create a new user in ubuntu (->system->administration->users), create the username and password and you have a new ftp account. You can make file availables for that ftp account dropping target files in /home/<newusername>
[/quote] 
A couple of things to add to that.  To change the default behavior of vsftp (anonymous access only) is pretty easy but you do need to edit [COLOR=Red]/etc/vsftpd.conf[/COLOR]. To enable local accounts or disable anonymous access change the lines with [COLOR=Blue]anonymous_enable=YES[/COLOR] and [COLOR=Blue]local_enable=NO[/COLOR] to fit your needs and then restart vsftpd with:
```

[COLOR=Red]sudo /etc/init.d/vsftpd restart[/COLOR]
``` 
Edit: Although this in not a graphical program, the way vsftpd.conf is written makes it about as easy and straight forward as it can be.  Just remember to restart the service using the command above to make your changes take effect.  Have fun.

---

### Post by Mike_SMD on 2006-05-08
Hello folks,

I should warn you in advance, though I'm learning... I'm still basically a Linux newbie. Talk real slow and I'll try to puzzle things out. That said.

All of the above seems pretty straightforward but I'm having a problem. I've done what was listed and my goal is NOT to have an anonymous ftp server enabled on an ongoing basis but rather to simply have an ftp server running on a 'as-needed' basis and this that I can restrict to a specific set of users. 

As an example, I want JoeBob to be able to access a folder on my machine so that he can download a bunch of music files or whatever. I don't want FredBob or DaveBob or whatever other fool is lurking out there to get in and do the same, nor do I want this access to be enabled by default... I want something that I can turn on and off when I want to and with minimal hassle.

Now following the advice above I seem to still have an anonymous only server running... can't quit figure out how to turn that function off or how to allow a non-anonymous login to take place. 

Here's what I get in terminal after making a system user called 'guest'...

mike@ubuntu:~$ ftp localhost
Connected to localhost.localdomain.
220 (vsFTPd 2.0.3)
Name (localhost:mike): guest
530 This FTP server is anonymous only.
Login failed.
ftp> quit
221 Goodbye.
mike@ubuntu:~$


And here's a copy of my vsftpd.conf file... (sorry it's so darn big)

# Example config file /etc/vsftpd.conf
#
# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.
#
#
# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
#listen=YES
#
# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive.
#listen_ipv6=YES
#
# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=NO
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
#write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
#local_umask=022
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
#anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
#anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
#chown_uploads=YES
#chown_username=whoever
#
# You may override where the log file goes if you like. The default is shown
# below.
#xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
#idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#data_connection_timeout=120
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=ftpsecure
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
#async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that turning on ascii_download_enable enables malicious remote parties
# to consume your I/O resources, by issuing the command "SIZE /big/file" in
# ASCII mode.
# These ASCII options are split into upload and download because you may wish
# to enable ASCII uploads (to prevent uploaded scripts etc. from breaking),
# without the DoS risk of SIZE and ASCII downloads. ASCII mangling should be
# on the client anyway..
#ascii_upload_enable=YES
#ascii_download_enable=YES
#
# You may fully customise the login banner string:
#ftpd_banner=Welcome to blah FTP service.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
#chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES
#
#
# Debian customization
#
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default.  These settings are more Debian-friendly.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/vsftpd.pem


-----

Any helpful suggestions?
I sort of gathered that I should have ended up with something like what I was after just following the above steps, but that's not really where I've ended up. As usual, I'm confused. Still like Linux but goddamn it's frustrating when what should be the simplest of things turns out to be the most ridiculous of hair-pulling trials.

A nice simple account of how to add a user for this server and then how to turn off the anonymous login would be greatly appreciated.

If there's any other information that you need just let me know,

Thanks for any help you can offer and have a very nice day!


Mike_SMD

---

### Post by z_diver on 2006-05-08
Mike,
I think you did everything correctly in your config file but did you restart the vsftpd service?
```
sudo /etc/init.d/vsftpd restart
``` To start and stop the service with a gui, uncheck vsftpd in the System menu > Administration > Services applet.  

If for some reason you want to use my favorite tool, the gnome-terminal I've provided the equivalent code below.  It may seem hard and frustrating in the begining but once you get used to using the terminal, it becomes most peoples favorite tool.  Like in my case, I have a nice dual g5 and I love Mac OSX but when someone cornered me and asked what my favorite program on the mac platform was, it took a while but I realized it was the terminal!!!
```
[COLOR=Green]sudo /etc/init.d/vsftpd start[/COLOR]
[COLOR=Red]sudo /etc/init.d/vsftpd stop[/COLOR]
``` p.s. Once you get used to using the terminal, you will find that you don't do a ton of typing in there.  Most of what you do is copying and pasting using the center mouse button while text is highlighted in another window or type a few letters, press TAB to see if it will automatically fill in the rest.  That and the 'UP ARROW' to find previously used commands help make it much more welcoming than it may at first seem.

---

### Post by mrwasabi on 2007-07-28
Hello folks,
I've been playing with ubuntu server for a few months now and I've finally decided that I want to setup a secure member only ftp server. I've looked over the vsftpd.conf file and it seems pretty straight forward I just have 1 question, if I want to change the default port how would I do that? I do not want this ftp server running on a standard port as my isp scans it as well as port 80. I also understand that when I create users on my server using:
sudo useradd -d /home/mybuddy -m mybuddy  - he can only access this folder "mybuddy" correct?

Also, what is the most secure protocol I can use to keep account information secure, TLS? Thanks in advance for any help you can provide.

---

### Post by Ampi on 2008-03-31
I set up a ftp server too... but I what I am sharing is a mounted volume. In my home I made a link to this volume but when I try (even as root) I get 550 error, fail to change directory.

---

