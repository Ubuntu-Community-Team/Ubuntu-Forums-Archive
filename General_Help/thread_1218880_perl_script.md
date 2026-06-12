---
title: "perl script"
date: 2009-07-21
forum: General Help
---

### Post by johnh10000 on 2009-07-21
Hi I thought I'd set up perl properly but....

I've done perl before, but can't recall..

Two simple scripts which I nicked off the web:

The obigatry hello world
--
#!/usr/bin/perl

print "Content-type: text/html\n\n";

print <<END_HTML;
<html>
<head></head>
<body>Hello, World!</body>
</html>
END_HTML
--
and printenv
--
#!/usr/bin/perl

print "Content-type: text/html\n\n";
print "<code>\n";

foreach $key (sort keys(%ENV)) {
  print "$key = $ENV{$key}<p>";
}
--
Which result in:
[Tue Jul 21 09:46:42 2009] [error] [client 192.168.1.3] (13)Permission denied: exec of '/usr/lib/cgi-bin/printenv.cgi' failed
[Tue Jul 21 09:46:42 2009] [error] [client 192.168.1.3] Premature end of script headers: printenv.cgi
[Tue Jul 21 09:47:57 2009] [error] [client 192.168.1.3] (13)Permission denied: exec of '/usr/lib/cgi-bin/printenv.cgi' failed
[Tue Jul 21 09:47:57 2009] [error] [client 192.168.1.3] Premature end of script headers: printenv.cgi
[Tue Jul 21 09:51:24 2009] [error] [client 192.168.1.3] (13)Permission denied: exec of '/usr/lib/cgi-bin/printenv.cgi' failed
[Tue Jul 21 09:51:24 2009] [error] [client 192.168.1.3] Premature end of script headers: printenv.cgi
[Tue Jul 21 09:55:42 2009] [error] [client 192.168.1.3] (13)Permission denied: exec of '/usr/lib/cgi-bin/hello.cgi' failed
[Tue Jul 21 09:55:43 2009] [error] [client 192.168.1.3] Premature end of script headers: hello.cgi

---

### Post by terrorsathan on 2009-07-21
Have you tried running the scripts as root?

Regards

---

### Post by indigest on 2009-07-21
You don't need to run these as root, but you do need to make them executable.  Try doing "chmod 744 helloworld.cgi" and see if you can execute it then.  Alternatively, you can also run "perl helloworld.cgi" if you don't want to make the Perl script executable for some reason.

---

### Post by johnh10000 on 2009-07-21
> **terrorsathan said:**
> Have you tried running the scripts as root?

Regards

No.  How would I do that?

I have changed the permissions to read write for all 666
And chown-nd the cgi-bin to my user account, the same as the website.

run from the command line hello, seems a bit broke, I'll fix that but print env seems to work
perl printenv.cgi
Content-type: text/html

<code>
COLORTERM = gnome-terminal<p>DBUS_SESSION_BUS_ADDRESS = unix:abstract=/tmp/dbus-18PVKxaJU8,guid=43cb47d7afcdc6bed74e49ce4a6508c6<p>DESKTOP_SESSION = GDM_Failsafe.GNOME<p>DISPLAY = :0.0<p>GDMSESSION = GDM_Failsafe.GNOME<p>GDM_LANG = en_GB.UTF-8<p>GDM_XSERVER_LOCATION = local<p>GNOME_DESKTOP_SESSION_ID = this-is-deprecated<p>GNOME_KEYRING_PID = 5099<p>GNOME_KEYRING_SOCKET = /tmp/keyring-1zpbse/socket<p>GTK_RC_FILES = /etc/gtk/gtkrc:/home/johnh10000/.gtkrc-1.2-gnome2<p>HISTCONTROL = ignoreboth<p>HOME = /home/johnh10000<p>LANG = en_GB.UTF-8<p>LESSCLOSE = /usr/bin/lesspipe %s %s<p>LESSOPEN = | /usr/bin/lesspipe %s<p>LOGNAME = johnh10000<p>LS_COLORS = no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:<p>MC_SID = 970<p>MC_TMPDIR = /tmp/mc-johnh10000<p>OLDPWD = /home/johnh10000/tux.isa-geek.org<p>ORBIT_SOCKETDIR = /tmp/orbit-johnh10000<p>PATH = /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games<p>PWD = /home/johnh10000/tux.isa-geek.org/cgi-bin<p>SESSION_MANAGER = local/tux:/tmp/.ICE-unix/5113<p>SHELL = /bin/bash<p>SHLVL = 2<p>SSH_AUTH_SOCK = /tmp/keyring-1zpbse/socket.ssh<p>TERM = xterm<p>USER = johnh10000<p>USERNAME = johnh10000<p>WINDOWID = 52428803<p>WINDOWPATH = 7<p>XAUTHORITY = /tmp/.gdm8FHHXU<p>XDG_DATA_DIRS = /usr/local/share/:/usr/share/:/usr/share/gdm/<p>XDG_SESSION_COOKIE = 2baf1d2d0356252edce7ccaf4a4efbf7-1248135364.191987-303067954<p>_ = /usr/bin/perl<p>johnh10000@tux:~/tux.isa-geek.org/cgi-bin$ ~
bash: /home/johnh10000: is a directory
[email]johnh10000@tux:~/tux.isa-geek.org[/email]/cgi-bin$ perl hello.cgi
Can't find string terminator "END_HTML" anywhere before EOF at hello.cgi line 5.
[email]johnh10000@tux:~/tux.isa-geek.org[/email]/cgi-bin$

---

### Post by terrorsathan on 2009-07-21
> **johnh10000 said:**
> 
[Tue Jul 21 09:46:42 2009] [error] [client 192.168.1.3] (13)Permission denied: exec of '/usr/lib/cgi-bin/printenv.cgi' failed
[Tue Jul 21 09:46:42 2009] [error] [client 192.168.1.3] Premature end of script headers: printenv.cgi
[Tue Jul 21 09:47:57 2009] [error] [client 192.168.1.3] (13)Permission denied: exec of '/usr/lib/cgi-bin/printenv.cgi' failed
[Tue Jul 21 09:47:57 2009] [error] [client 192.168.1.3] Premature end of script headers: printenv.cgi
[Tue Jul 21 09:51:24 2009] [error] [client 192.168.1.3] (13)Permission denied: exec of '/usr/lib/cgi-bin/printenv.cgi' failed
[Tue Jul 21 09:51:24 2009] [error] [client 192.168.1.3] Premature end of script headers: printenv.cgi
[Tue Jul 21 09:55:42 2009] [error] [client 192.168.1.3] (13)Permission denied: exec of '/usr/lib/cgi-bin/hello.cgi' failed
[Tue Jul 21 09:55:43 2009] [error] [client 192.168.1.3] Premature end of script headers: hello.cgi

Anyway, looks like you were trying to run it using a www server? If you did, you wouldn't need to add the line "#!/usr/bin/perl".

> **johnh10000 said:**
> No.  How would I do that?
Either
```
sudo ./script.pl
```
or
```
sudo perl script.pl
```

And btw you don't need to chmod it 666 to make it executable, do it like that:
```
chmod +x script.pl
```

Regards

---

### Post by johnh10000 on 2009-07-21
> **terrorsathan said:**
> Anyway, looks like you were trying to run it using a www server? If you did, you wouldn't need to add the line "#!/usr/bin/perl".
removed that

Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.
Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch mod_ruby/1.2.6 Ruby/1.8.7(2008-08-11) Server at tux.isa-geek.org Port 80

Either
```
sudo ./script.pl
```
or
```
sudo perl script.pl
```

Regards

sudo perl hello.cgi
Semicolon seems to be missing at hello.cgi line 7.
syntax error at hello.cgi line 6, near "head>"
Can't find string terminator "END_HTML" anywhere before EOF at hello.cgi line 11.
[email]johnh10000@tux:~/tux.isa-geek.org[/email]/cgi-bin$ 

sudo perl printenv.cgi
Content-type: text/html

<code>
COLORTERM = gnome-terminal<p>DISPLAY = :0.0<p>HOME = /home/johnh10000<p>LANG = en_GB.UTF-8<p>LOGNAME = root<p>LS_COLORS = no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:<p>PATH = /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin<p>SHELL = /bin/bash<p>SUDO_COMMAND = /usr/bin/perl printenv.cgi<p>SUDO_GID = 1000<p>SUDO_UID = 1000<p>SUDO_USER = johnh10000<p>TERM = xterm<p>USER = root<p>USERNAME = root<p>XAUTHORITY = /tmp/.gdm8FHHXU<p>johnh10000@tux:~/tux.isa-geek.org/cgi-bin$

---

### Post by terrorsathan on 2009-07-21
> **johnh10000 said:**
> sudo perl hello.cgi
Semicolon seems to be missing at hello.cgi line 7.
syntax error at hello.cgi line 6, near "head>"
Can't find string terminator "END_HTML" anywhere before EOF at hello.cgi line 11.
[email]johnh10000@tux:~/tux.isa-geek.org[/email]/cgi-bin$ 

sudo perl printenv.cgi
Content-type: text/html

<code>
COLORTERM = gnome-terminal<p>DISPLAY = :0.0<p>HOME = /home/johnh10000<p>LANG = en_GB.UTF-8<p>LOGNAME = root<p>LS_COLORS = no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:<p>PATH = /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin<p>SHELL = /bin/bash<p>SUDO_COMMAND = /usr/bin/perl printenv.cgi<p>SUDO_GID = 1000<p>SUDO_UID = 1000<p>SUDO_USER = johnh10000<p>TERM = xterm<p>USER = root<p>USERNAME = root<p>XAUTHORITY = /tmp/.gdm8FHHXU<p>johnh10000@tux:~/tux.isa-geek.org/cgi-bin$

"sudo perl printenv.cgi" seems to work, right? Looks like there's a syntax error in your "hello.cgi". Are you sure its content looks like that:
```
#!/usr/bin/perl

print "Content-type: text/html\n\n";
print <<END_HTML
<html>
<head></head>
<body>Hello, World!</body>
</html>
END_HTML
```

Regards

---

### Post by johnh10000 on 2009-07-21
> **terrorsathan said:**
> "sudo perl printenv.cgi" seems to work, right? 
> 
Well it works fine out of the browser, with or without the sudo

[QUOTE]
Looks like there's a syntax error in your "hello.cgi". Are you sure its content looks like that:
```
#!/usr/bin/perl

print "Content-type: text/html\n\n";
print <<END_HTML
<html>
<head></head>
<body>Hello, World!</body>
</html>
END_HTML
```

it does now ;)

And...
0;johnh10000@tux: ~/tux.isa-geek.org/cgi-binjohnh10000@tux:~/tux.isa-gee
[email]johnh10000@tux:~/tux.isa-geek.org[/email]/cgi-bin$ perl hello.cgi
Can't find string terminator "END_HTML" anywhere before EOF at hello.cgi line 4.
[email]johnh10000@tux:~/tux.isa-geek.org[/email]/cgi-bin$ 

--
I just checked and that mod-perl thingy is installed, so I don't know why it isn't working in the browser.

BTW [http://tux.isa-geek.org/cgi-bin/hello.cgi](http://tux.isa-geek.org/cgi-bin/hello.cgi)


Regards

---

