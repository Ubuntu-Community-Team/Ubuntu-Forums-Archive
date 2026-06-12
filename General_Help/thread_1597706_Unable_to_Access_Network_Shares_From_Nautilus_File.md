---
title: "Unable to Access Network Shares From Nautilus File Manager"
date: 2010-10-15
forum: General Help
---

### Post by silverbullet763 on 2010-10-15
I'm running 64 bit Lucid on a HTPC that is networked with a Windows 7 64 bit laptop. Up until this morning, sharing media between these two worked fine. When I attempted to connect through Rhythmbox to play music, the computer couldn't find the files. I attempted to access the network through Nautilus and it was unable to mount the location. So I tried the Create Launcher command and created a link of the network on the desktop. I was prompted to login and it worked perfectly :confused: This has happened once before and the only way to fix it was to reinstall Ubuntu. I would very much like to avoid that if possible as the system is setup perfectly. I wouldn't bother with the issue if it didn't prevent me from adding my music files to Rhythmbox. I have run findsmb as well as smbtree. Smbtree returned nothing and findsmb had a dotted line with nothing underneath. Nothing has been removed. I did install security updates this morning, but since it has happened before, I am more inclined to thing it is a bug or conflict somewhere. I have read a few threads where this was happening to others, but they didn't seem to find a fix either. Any help is greatly appreciated.

---

### Post by Woody1987 on 2010-10-15
I have had this problem before several times and it was always the fault of Windows. What i did was just mess with the Windows networking settings until it worked by chance.

---

### Post by silverbullet763 on 2010-10-15
> **Woody1987 said:**
> I have had this problem before several times and it was always the fault of Windows. What i did was just mess with the Windows networking settings until it worked by chance.

The odd thing is nothing appears wrong with either one. I can ping them both and they both receive the packets so it really is a strange thing. I have adjusted the settings on both and unfortunately it just will not work. Is there a work around for this that anyone can think of? I know when Windows 7 installed updates it updated something related to SMB in the registry. Anyone noticed a similar issue?

---

### Post by luvshines on 2010-10-15
Though I am not sure but are there any logs for nautilus's failure to mount in ~/.xsession-errors

Are you able to access through terminal:
```

## List the share. Drop -U<un>%<up> if guest allowed
smbclient -L <server-ip> -U<username>%<passwd>

## Access the share. Drop -U<un>%<up> if guest allowed
smbclient //<server-ip>/<share-name> -U<username>%<passwd>

```

---

### Post by silverbullet763 on 2010-10-15
> **luvshines said:**
> Though I am not sure but are there any logs for nautilus's failure to mount in ~/.xsession-errors

Are you able to access through terminal:
```

## List the share. Drop -U<un>%<up> if guest allowed
smbclient -L <server-ip> -U<username>%<passwd>

## Access the share. Drop -U<un>%<up> if guest allowed
smbclient //<server-ip>/<share-name> -U<username>%<passwd>

```

No there wasn't anything in xsession.

The terminal lists the shares but says the session request failed Called Name Not Present
It also says NetBIOS over TCP is Disabled No workgroup available
I have NetBIOS enabled on the Windows Machine?

---

### Post by luvshines on 2010-10-16
Any success yet ??

Can you try enabling netbios over TCP/IP from windows 7:
[http://ttcshelbyville.wordpress.com/2009/12/17/enable-netbios-over-tcpip/](http://ttcshelbyville.wordpress.com/2009/12/17/enable-netbios-over-tcpip/)

---

### Post by silverbullet763 on 2010-10-16
> **luvshines said:**
> Any success yet ??

Can you try enabling netbios over TCP/IP from windows 7:
[http://ttcshelbyville.wordpress.com/2009/12/17/enable-netbios-over-tcpip/](http://ttcshelbyville.wordpress.com/2009/12/17/enable-netbios-over-tcpip/)

No success yet. Netbios has been enabled from the beginning. That's why that error makes little sense at this point. I do need to find the root of this issue. Can't keep reinstalling all the time lol.

---

### Post by Morbius1 on 2010-10-16
Excuse the interruption,  but the Win7 machine you are trying to access - does it by any chance have Windows Live Sign-In Assistant installed?

You might consider uninstalling it as it is a known bug with Samba:
[http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527)
[https://bugzilla.samba.org/show_bug.cgi?id=7577](https://bugzilla.samba.org/show_bug.cgi?id=7577)

PS: luvshines. Do you never sleep ?

---

### Post by silverbullet763 on 2010-10-16
> **Morbius1 said:**
> Excuse the interruption,  but the Win7 machine you are trying to access - does it by any chance have Windows Live Sign-In Assistant installed?

You might consider uninstalling it as it is a known bug with Samba:
[http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527)
[https://bugzilla.samba.org/show_bug.cgi?id=7577](https://bugzilla.samba.org/show_bug.cgi?id=7577)

PS: luvshines. Do you never sleep ?

Nope I had to remove that back when I first setup the HTPC in order to begin sharing. No interruption at all. Anyone with potential solutions is more than welcome to chime in :)

---

### Post by luvshines on 2010-10-16
:lolflag: @Morbius1

Nice to see you again, I was just logging off. It's already 5:00 AM in India but it is a weekend so I am excused else I crash at 3 usually :D

PS: I hate to sleep and try not to, but fall unconscious newayz

---

### Post by luvshines on 2010-10-16
This one is also stuck in similar issue:
[http://ubuntuforums.org/showthread.php?t=1598185](http://ubuntuforums.org/showthread.php?t=1598185)
```

smbclient -L 192.168.1.3
Enter military's password: 
Domain=[LIONESS] OS=[Windows 7 Ultimate 7600 Service Pack 2] Server=[Windows 7 Ultimate 6.1]

    Sharename       Type      Comment
    ---------       ----      -------
Error returning browse list: NT_STATUS_NOT_SUPPORTED
session request to 192.168.1.3 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available

```

Don't know what NT_STATUS_NOT_SUPPORTED means. Can a different Domain be an issue

---

### Post by silverbullet763 on 2010-10-16
> **luvshines said:**
> This one is also stuck in similar issue:
[http://ubuntuforums.org/showthread.php?t=1598185](http://ubuntuforums.org/showthread.php?t=1598185)
```

smbclient -L 192.168.1.3
Enter military's password: 
Domain=[LIONESS] OS=[Windows 7 Ultimate 7600 Service Pack 2] Server=[Windows 7 Ultimate 6.1]

    Sharename       Type      Comment
    ---------       ----      -------
Error returning browse list: NT_STATUS_NOT_SUPPORTED
session request to 192.168.1.3 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available

```Don't know what NT_STATUS_NOT_SUPPORTED means. Can a different Domain be an issue

The portion here:

session request to 192.168.1.3 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available

Is identical to what I get as well. My shares appear in the list, however.
NT_STATUS_NOT_SUPPORTED was a bug in samba apparently.

_[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/472681](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/472681)_[]("http://www.evanhoffman.com/evan/2009/10/24/error-returning-browse-list-nt_status_not_supported/")

---

### Post by silverbullet763 on 2010-10-16
I'm wondering if I'm looking at this correctly. The shortcut on the ubuntu desktop displays all the shares as it should. I have full access to all shared media as long as it is through that shortcut. So that would imply that the Windows 7 machine is functioning properly and allowing them to be accessed. Ubuntu can obviously see the shares, so the communication is given and received accordingly. The problem comes in when Nautilus is entered into the equation. Something would seem to be conflicting or preventing it from mounting the shares appropriately, as it is able to be mounted through the desktop. The question here is what? Is there something I'm obviously missing here?

---

### Post by silverbullet763 on 2010-10-16
Update: Small victory here anyway. After playing with Rhythmbox a little I was able to clear the library and get it to use the desktop mount point in order to add all the files and make them usable again. This still doesn't solve the issue of it not mounting directly in the Network file manager area, but it is a workaround until we can figure out what in the world is going on. For folks searching for a workaround or solution try this:

1) Right click desktop and select Create Launcher
2) Change Type to Location
3) I named mine Media, but you can use whatever you want.
4) Type in the address of your shares. ex: smb://192.168.x.x
5) Hit OK.
6) When you double click the Launcher a window should appear and ask you to enter credentials username, password, etc). My username and workgroup were already filled in and all I needed to do was enter the password. I also allow it to remember the password until I log out.

Then once that was done I went to Rhythmbox. My library had the tracks from the original Network location in Nautilus that for god knows what reason is failing, so I went to ~/.local/share/rhythmbox/rhythmdb.xml and moved that to the trash.Make sure Rhythmbox is closed first. Also make sure the share with your music is mounted through the desktop. Then go ahead and reopen Rhythmbox. Your library should be empty now. Go to Music--Import File and add the desktop mount point. 

Creating a Launcher on the desktop should work with all of your files such as documents, music, pics, etc. At least you will have the access required. I do hope to find out why it will only work like this. I still think the problem is a conflict or bug in the file manager. Hope the mini tutorial helps someone and if anyone has any idea about the file manager issue, please feel free to post!:)

---

### Post by psihokiller4 on 2010-10-17
ok I fixed mine or should I say updates have fixed it

well if you have to go to updates witch mostly destroyed my OS use only main updates
otherwise I'd never go to updates if I wouldn't already destroy my system

EDIT
better: if you guys are interested in what packages I have installed and to figure out from that:

aptitude -F '%?p %?V' search '~i'

```
libxdmcp-dev                                                           1:1.0.2-3
libxdmcp6                                                              1:1.0.2-3
libxerces2-java                                                   2.9.1-4ubuntu1
libxext-dev                                                  2:1.0.99.1-0ubuntu4
libxext6                                                     2:1.0.99.1-0ubuntu4
libxfixes-dev                                                    1:4.0.3-2build1
libxfixes3                                                       1:4.0.3-2build1
libxfont1                                                       1:1.4.0-1ubuntu1
libxft-dev                                                       2.1.13-3ubuntu1
libxft2                                                          2.1.13-3ubuntu1
libxi-dev                                                       2:1.2.1-2ubuntu1
libxi6                                                          2:1.2.1-2ubuntu1
libxinerama-dev                                                        2:1.0.3-2
libxinerama1                                                           2:1.0.3-2
libxkbfile1                                                     1:1.0.5-1ubuntu2
libxklavier15                                                       4.0-0ubuntu5
libxml-parser-perl                                                2.36-1.1build2
libxml-twig-perl                                                 1:3.32-3ubuntu1
libxml-xpath-perl                                                         1.13-6
libxml2                                                      2.7.5.dfsg-1ubuntu1
libxml2-dev                                                  2.7.5.dfsg-1ubuntu1
libxml2-utils                                                2.7.5.dfsg-1ubuntu1
libxmu6                                                                2:1.0.4-2
libxmuu1                                                               2:1.0.4-2
libxp6                                                            1:1.0.0.xsf1-2
libxpm4                                                                1:3.5.7-2
libxrandr-dev                                                          2:1.3.0-2
libxrandr2                                                             2:1.3.0-2
libxrender-dev                                                  1:0.9.4-2ubuntu1
libxrender1                                                     1:0.9.4-2ubuntu1
libxres1                                                               2:1.0.3-2
libxslt1.1                                                       1.1.24-2ubuntu2
libxss1                                                                1:1.1.3-1
libxt-dev                                                       1:1.0.5-3ubuntu1
libxt6                                                          1:1.0.5-3ubuntu1
libxtrap6                                                        2:1.0.0-5build1
libxtst6                                                        2:1.0.3-1ubuntu2
libxv1                                                                 2:1.0.4-1
libxvmc1                                                        2:1.0.4-2ubuntu2
libxxf86dga1                                                     2:1.0.2-1build1
libxxf86misc1                                                          1:1.0.1-3
libxxf86vm1                                                     1:1.0.2-1ubuntu1
libzephyr4                                                         3.0~rc.2544-1
linux-firmware                                                              1.24
linux-generic                                                       2.6.31.22.35
linux-headers-2.6.31-14                                             2.6.31-14.48
linux-headers-2.6.31-14-generic                                     2.6.31-14.48
linux-headers-2.6.31-22                                             2.6.31-22.65
linux-headers-2.6.31-22-generic                                     2.6.31-22.65
linux-headers-generic                                               2.6.31.22.35
linux-image-2.6.31-14-generic                                       2.6.31-14.48
linux-image-2.6.31-22-generic                                       2.6.31-22.65
linux-image-generic                                                 2.6.31.22.35
linux-libc-dev                                                      2.6.31-22.65
linux-sound-base                                            1.0.20+dfsg-1ubuntu5
lksctp-tools                                                       1.0.10+dfsg-1
locales                                                        2.9+git20090617-3
lockfile-progs                                                            0.1.13
login                                                         1:4.1.4.1-1ubuntu2
logrotate                                                         3.7.8-4ubuntu1
lp-solve                                                              5.5.0.13-6
lsb-base                                                            4.0-0ubuntu5
lsb-release                                                         4.0-0ubuntu5
lshw                                                                     02.14-1
lsof                                                               4.81.dfsg.1-1
ltrace                                                            0.5.3-2ubuntu2
lzma                                                              4.43-14ubuntu1
m17n-contrib                                                             1.1.9-1
m17n-db                                                                  1.5.4-1
m4                                                                      1.4.13-2
make                                                                      3.81-6
makedev                                                                 2.3.1-88
man-db                                                                   2.5.6-2
manpages                                                                  3.21-1
mawk                                                             1.3.3-15ubuntu1
media-player-info                                                     3-0ubuntu1
memtest86+                                                         2.11-3ubuntu5
mesa-common-dev                                                   7.6.0-1ubuntu4
mesa-utils                                                        7.6.0-1ubuntu4
metacity                                                       1:2.28.0-0ubuntu1
metacity-common                                                1:2.28.0-0ubuntu1
mime-support                                                       3.46-1ubuntu1
min12xxw                                                          0.0.9-3ubuntu1
mlocate                                                                 0.21.1-2
mobile-broadband-provider-info                                 20091009-0ubuntu1
modemmanager                            0.2.git.20091014t233208.16f3e00-0ubuntu1
module-init-tools                                                         3.10-3
mono-2.0-gac                                                      2.4.2.3+dfsg-2
mono-gac                                                          2.4.2.3+dfsg-2
mono-runtime                                                      2.4.2.3+dfsg-2
mount                                                              2.16-1ubuntu5
mountall                                                                     1.0
mousetweaks                                                      2.28.1-0ubuntu1
mscompress                                                                 0.3-3
mtools                                                                  4.0.10-1
mtr-tiny                                                                  0.75-2
myspell-en-au                                                            2.1-3.1
myspell-en-gb                                                   1:3.0.1-8ubuntu1
myspell-en-za                                                   1:3.0.1-8ubuntu1
mysql-common                                                   5.1.37-1ubuntu5.4
nano                                                                     2.0.9-2
nasm                                                                   2.05.01-1
nautilus                                                       1:2.28.1-0ubuntu1
nautilus-data                                                  1:2.28.1-0ubuntu1
nautilus-sendto                                                  2.28.0-0ubuntu1
nautilus-share                                                          0.7.2-12
ncurses-base                                               5.7+20090803-2ubuntu2
ncurses-bin                                                5.7+20090803-2ubuntu2
net-tools                                                         1.60-23ubuntu1
netbase                                                              4.35ubuntu2
netcat                                                                   1.10-38
netcat-traditional                                                       1.10-38
network-manager                       0.8~a~git.20091013t193206.679d548-0ubuntu1
network-manager-gnome                 0.8~a~git.20091014t134532.4033e62-0ubuntu1
notify-osd                                                       0.9.24-0ubuntu1
notify-osd-icons                                                             0.3
ntfs-3g                                                      1:2009.4.4-1ubuntu4
ntpdate                                                1:4.2.4p6+dfsg-1ubuntu5.1
nvidia-173-modaliases                                         173.14.20-0ubuntu5
nvidia-185-modaliases                                         185.18.36-0ubuntu9
nvidia-96-modaliases                                           96.43.13-0ubuntu6
nvidia-common                                                             0.2.15
obex-data-server                                                   0.4.4-2build1
obexd-client                                                       0.14-0ubuntu1
odbcinst1debian1                                                2.2.11-16ubuntu1
onboard                                                          0.92.0-0ubuntu3
openjdk-6-jre                                         6b18-1.8.1-0ubuntu1~9.10.1
openjdk-6-jre-headless                                6b18-1.8.1-0ubuntu1~9.10.1
openjdk-6-jre-lib                                     6b18-1.8.1-0ubuntu1~9.10.1
openoffice.org-base-core                                      1:3.1.1-5ubuntu1.2
openoffice.org-calc                                           1:3.1.1-5ubuntu1.2
openoffice.org-common                                         1:3.1.1-5ubuntu1.2
openoffice.org-core                                           1:3.1.1-5ubuntu1.2
openoffice.org-draw                                           1:3.1.1-5ubuntu1.2
openoffice.org-emailmerge                                     1:3.1.1-5ubuntu1.2
openoffice.org-gnome                                          1:3.1.1-5ubuntu1.2
openoffice.org-gtk                                            1:3.1.1-5ubuntu1.2
openoffice.org-help-en-us                                       1:3.1.1-4ubuntu1
openoffice.org-hyphenation                                                   0.3
openoffice.org-hyphenation-en-us                                           2.4-4
openoffice.org-impress                                        1:3.1.1-5ubuntu1.2
openoffice.org-math                                           1:3.1.1-5ubuntu1.2
openoffice.org-style-human                                    1:3.1.1-5ubuntu1.2
openoffice.org-thesaurus-en-au                                           2.1-3.1
openoffice.org-thesaurus-en-us                                  1:3.0.1-8ubuntu1
openoffice.org-writer                                         1:3.1.1-5ubuntu1.2
openprinting-ppds                                              20090825-0ubuntu4
openssh-client                                                  1:5.1p1-6ubuntu2
openssl                                                       0.9.8g-16ubuntu3.3
orbit2                                                             1:2.14.17-0.1
os-prober                                                                   1.35
parted                                             1.8.8.git.2009.06.03-1ubuntu6
passwd                                                        1:4.1.4.1-1ubuntu2
patch                                                                    2.5.9-5
pciutils                                                       1:3.0.0-4ubuntu13
pcmciautils                                                         014-4ubuntu3
perl                                                            5.10.0-24ubuntu4
perl-base                                                       5.10.0-24ubuntu4
perl-modules                                                    5.10.0-24ubuntu4
pkg-config                                                          0.22-1build1
pm-utils                                                          1.2.5-2ubuntu7
pnm2ppa                                                         1.12-16.2ubuntu2
po-debconf                                                                1.0.16
policykit-1                                                        0.94-1ubuntu1
policykit-1-gnome                                             0.94-1+1git.230873
poppler-utils                                                  0.12.0-0ubuntu2.1
popularity-contest                                                   1.48ubuntu1
powermgmt-base                                                         1.30+nmu1
ppp                                            2.4.5~git20081126t100229-0ubuntu2
pppconfig                                                          2.3.18ubuntu2
pppoeconf                                                            1.18ubuntu1
procps                                                          1:3.2.8-1ubuntu3
protobuf-compiler                                               2.0.3-2.2ubuntu2
psfontmgr                                                     0.11.10-0.2ubuntu1
psmisc                                                                    22.7-1
pulseaudio                                                     1:0.9.19-0ubuntu4
pulseaudio-esound-compat                                       1:0.9.19-0ubuntu4
pulseaudio-module-bluetooth                                    1:0.9.19-0ubuntu4
pulseaudio-module-gconf                                        1:0.9.19-0ubuntu4
pulseaudio-module-udev                                         1:0.9.19-0ubuntu4
pulseaudio-module-x11                                          1:0.9.19-0ubuntu4
pulseaudio-utils                                               1:0.9.19-0ubuntu4
pxljr                                                               1.1-0ubuntu7
python                                                        2.6.4~rc1-0ubuntu1
python-apport                                                     1.9.3-0ubuntu4
python-apt                                                       0.7.13.2ubuntu4
python-aptdaemon                                            0.10+bzr264-0ubuntu1
python-aptdaemon-gtk                                        0.10+bzr264-0ubuntu1
python-avahi                                                   0.6.25-1ubuntu5.2
python-brlapi                                                       4.0-7ubuntu2
python-cairo                                                      1.8.6-1ubuntu1
python-central                                                     0.6.11ubuntu9
python-configglue                                                0.2dev-0ubuntu2
python-couchdb                                                             0.6-1
python-crypto                                               2.0.1+dfsg1-4ubuntu1
python-cups                                                      1.9.46-0ubuntu2
python-cupshelpers                                   1.1.12+git20090826-0ubuntu8
python-dbus                                                      0.83.0-1ubuntu2
python-debian                                                      0.1.14ubuntu1
python-desktopcouch                                                 0.5-0ubuntu1
python-desktopcouch-records                                         0.5-0ubuntu1
python-dev                                                    2.6.4~rc1-0ubuntu1
python-fstab                                                        1.4-0ubuntu1
python-gconf                                                     2.28.0-0ubuntu1
python-gdbm                                                       2.6.3-0ubuntu1
python-glade2                                                    2.16.0-0ubuntu1
python-gmenu                                                   2.28.0.1-0ubuntu1
python-gnome2                                                    2.28.0-0ubuntu1
python-gnomeapplet                                               2.28.0-0ubuntu1
python-gnomecanvas                                               2.28.0-0ubuntu1
python-gnomekeyring                                              2.28.0-0ubuntu1
python-gnupginterface                                             0.3.2-9ubuntu2
python-gobject                                                   2.18.0-0ubuntu2
python-gobject-dev                                               2.18.0-0ubuntu2
python-gst0.10                                                         0.10.17-1
python-gtk2                                                      2.16.0-0ubuntu1
python-gtk2-dev                                                  2.16.0-0ubuntu1
python-gtk2-doc                                                  2.16.0-0ubuntu1
python-gtkhtml2                                           2.25.3-3ubuntu1.9.10.1
python-gtksourceview2                                                    2.8.0-1
python-httplib2                                                   0.4.0-0ubuntu2
python-ibus                                              1.2.0.20090927-2ubuntu1
python-imaging                                                    1.1.6-3ubuntu1
python-launchpad-integration                                              0.1.26
python-launchpadlib                                               1.5.1-0ubuntu1
python-lazr-restfulclient                                         0.9.3-0ubuntu3
python-lazr-uri                                                     1.0-0ubuntu1
python-libxml2                                               2.7.5.dfsg-1ubuntu1
python-louis                                                      1.7.0-1ubuntu1
python-minimal                                                2.6.4~rc1-0ubuntu1
python-newt                                                     0.52.10-4ubuntu1
python-notify                                                      0.1.1-2build2
python-numpy                                                           1:1.3.0-3
python-oauth                                               1.0a~svn1124-0ubuntu2
python-openssl                                                             0.9-1
python-pam                                                       0.4.2-12ubuntu3
python-papyon                                                     0.4.3-1ubuntu1
python-pkg-resources                                              0.6c9-0ubuntu5
python-problem-report                                             1.9.3-0ubuntu4
python-protobuf                                                 2.0.3-2.2ubuntu2
python-pyatspi                                                   1.28.1-0ubuntu1
python-pygame                                                             <none>
python-pyinotify                                                  0.8.6-2ubuntu2
python-pyorbit                                                   2.24.0-0ubuntu3
python-rdflib                                                     2.4.0-5ubuntu1
python-rsvg                                                      2.28.0-0ubuntu1
python-serial                                                              2.3-1
python-sexy                                                       0.1.9-1ubuntu2
python-simplejson                                                        2.0.9-1
python-smbc                                                       1.0.6-0ubuntu2
python-software-properties                                                0.75.4
python-speechd                             0.6.7+git20090914~unofficial-0ubuntu4
python-support                                                      1.0.3ubuntu1
python-telepathy                                                       0.15.11-1
python-twisted-bin                                                       8.2.0-3
python-twisted-core                                                      8.2.0-3
python-twisted-names                                              8.2.0-1ubuntu2
python-twisted-web                                                8.2.0-2ubuntu1
python-ubuntuone-client                                           1.0.2-0ubuntu1
python-ubuntuone-storageprotocol                                  1.0.0-0ubuntu1
python-uno                                                    1:3.1.1-5ubuntu1.2
python-virtkey                                                       0.50ubuntu2
python-vte                                                   1:0.22.2-0ubuntu2.1
python-wadllib                                                    1.1.2-0ubuntu1
python-webkit                                                            1.1.5-1
python-xapian                                                     1.0.14-1build1
python-xdg                                                       0.15-1.1ubuntu5
python-xkit                                                                0.4.2
python-zope.interface                                                    3.5.2-1
python2.6                                                     2.6.4~rc2-0ubuntu1
python2.6-dev                                                 2.6.4~rc2-0ubuntu1
python2.6-minimal                                             2.6.4~rc2-0ubuntu1
radeontool                                              1.5+git76606164-0ubuntu2
raptor-utils                                                            1.4.19-1
rarian-compat                                                     0.8.1-2ubuntu3
rdesktop                                                          1.6.0-2ubuntu2
readline-common                                                            6.0-5
redland-utils                                                            1.0.9-2
rhino                                                             1.7R2-1ubuntu1
rhythmbox                                                        0.12.5-0ubuntu4
rsync                                                             3.0.6-1ubuntu1
rsyslog                                                           4.2.0-2ubuntu5
ruby                                                                         4.2
ruby-gnome2                                                               <none>
ruby-gnome2-dev                                                           <none>
ruby1.8                                                              1.8.7.174-1
ruby1.8-dev                                                          1.8.7.174-1
samba-common                                                  2:3.4.0-3ubuntu5.7
samba-common-bin                                              2:3.4.0-3ubuntu5.7
same-gnome                                                     1:2.28.0-0ubuntu1
sane-utils                                                       1.0.20-4ubuntu3
screen                                                           4.0.3-13ubuntu4
screen-resolution-extra                                                     0.11
screensaver-default-images                                                 0.2-1
seahorse                                                         2.28.1-0ubuntu1
sed                                                                      4.2.1-1
sgml-base                                                                   1.26
sgml-data                                                                  2.0.3
shared-mime-info                                                   0.70-0ubuntu1
smartdimmer                                                       0.8b4-1ubuntu2
smbclient                                                     2:3.4.0-3ubuntu5.7
software-center                                                            1.0.2
software-properties-gtk                                                   0.75.4
speech-dispatcher                          0.6.7+git20090914~unofficial-0ubuntu4
splix                                                             2.0.0-2ubuntu2
sreadahead                                                                 1.0-5
ssh-askpass-gnome                                               1:5.1p1-6ubuntu2
ssl-cert                                                           1.0.23ubuntu2
strace                                                           4.5.18-1ubuntu2
sudo                                                            1.7.0-1ubuntu2.5
sun-java6-bin                                                             <none>
sun-java6-jre                                                             <none>
swfdec-gnome                                                              <none>
synaptic                                                           0.62.7ubuntu6
syslinux                                                    2:3.63+dfsg-2ubuntu3
system-config-printer-common                         1.1.12+git20090826-0ubuntu8
system-config-printer-gnome                          1.1.12+git20090826-0ubuntu8
system-config-printer-udev                           1.1.12+git20090826-0ubuntu8
system-tools-backends                                                    2.8.2-1
sysv-rc                                                        2.87dsf-4ubuntu11
sysvinit-utils                                                 2.87dsf-4ubuntu11
tar                                                                       1.22-1
tasksel                                                             2.73ubuntu23
tasksel-data                                                        2.73ubuntu23
tcl8.4                                                                  8.4.19-3
tcpd                                                                    7.6.q-16
tcpdump                                                           4.0.0-2ubuntu2
telepathy-butterfly                                               0.5.2-0ubuntu1
telepathy-gabble                                                         0.8.7-1
telepathy-haze                                                           0.3.2-1
telepathy-idle                                                           0.1.5-1
telepathy-mission-control-5                                              5.3.1-1
telepathy-salut                                                         0.3.10-1
telnet                                                                   0.17-36
time                                                                      1.7-23
tk8.4                                                                   8.4.19-3
tomboy                                                            1.0.0-0ubuntu2
toshset                                                                   1.75-1
totem                                                            2.28.1-0ubuntu4
totem-common                                                     2.28.1-0ubuntu4
totem-mozilla                                                    2.28.1-0ubuntu4
totem-plugins                                                    2.28.1-0ubuntu4
transmission-common                                              1.75-0ubuntu2.2
transmission-gtk                                                 1.75-0ubuntu2.2
tsclient                                                          0.150-2ubuntu2
tsconf                                                                     1.0-7
ttf-dejavu-core                                                           2.29-2
ttf-freefont                                                          20090104-2
ttf-indic-fonts-core                                              1:0.5.4ubuntu2
ttf-kacst                                                              2.0+mry-1
ttf-lao                                                           0.0.20060226-2
ttf-liberation                                          1.05.1.20090721-0ubuntu1
ttf-mscorefonts-installer                                                 <none>
ttf-opensymbol                                                1:3.1.1-5ubuntu1.2
ttf-symbol-replacement                                                    <none>
ttf-tahoma-replacement                                                    <none>
ttf-thai-tlwg                                                  1:0.4.13-1ubuntu1
ttf-unfonts-core                                                  1.0.1-7ubuntu1
ttf-vlgothic                                                          20090612-2
ttf-wqy-zenhei                                                   0.8.38-1ubuntu1
tzdata                                                            2009o-1ubuntu2
tzdata-java                                                       2009o-1ubuntu2
ubufox                                                   0.9~rc2-0ubuntu0.9.10.1
ubuntu-artwork                                                                51
ubuntu-desktop                                                             1.175
ubuntu-docs                                                              9.10.11
ubuntu-keyring                                                        2009.08.28
ubuntu-minimal                                                             1.175
ubuntu-sounds                                                               0.12
ubuntu-standard                                                            1.175
ubuntu-system-service                                                     0.1.16
ubuntu-wallpapers                                                           0.30
ubuntu-xsplash-artwork                                            0.8.4-0ubuntu1
ubuntuone-client                                                  1.0.2-0ubuntu1
ubuntuone-client-gnome                                            1.0.2-0ubuntu1
ucf                                                                3.0018ubuntu1
udev                                                                      147~-6
ufw                                                                0.29-4ubuntu1
unattended-upgrades                                                  0.52ubuntu1
unixodbc                                                        2.2.11-16ubuntu1
uno-libs3                                              1.5.1+OOo3.1.1-5ubuntu1.2
unzip                                                                      6.0-1
update-inetd                                                                4.31
update-manager                                                         1:0.126.6
update-manager-core                                                    1:0.126.6
update-notifier                                                             0.90
update-notifier-common                                                      0.90
upstart                                                                 0.6.3-10
ure                                                    1.5.1+OOo3.1.1-5ubuntu1.2
usb-creator-common                                                        0.2.12
usb-creator-gtk                                                           0.2.12
usbutils                                                           0.82-0ubuntu1
usplash                                                                   0.5.49
usplash-theme-ubuntu                                                        0.27
util-linux                                                         2.16-1ubuntu5
uuid-runtime                                                       2.16-1ubuntu5
vbetool                                                                    1.1-2
vim-common                                                    2:7.2.245-2ubuntu2
vim-tiny                                                      2:7.2.245-2ubuntu2
vinagre                                                          2.28.1-0ubuntu1
vino                                                             2.28.1-0ubuntu2
vzctl                                                                     <none>
vzdump                                                                    <none>
vzquota                                                                   <none>
w3m                                                             0.5.2-2ubuntu1.1
wamerican                                                                    6-3
wbritish                                                                     6-3
wget                                                           1.11.4-2ubuntu2.1
whiptail                                                        0.52.10-4ubuntu1
whois                                                              4.7.34ubuntu2
winbind                                                       2:3.4.0-3ubuntu5.7
wine1.2                                                                   <none>
wine1.2-gecko                                                             <none>
wireless-crda                                                               1.10
wireless-tools                                                       29-2ubuntu6
wodim                                                           9:1.1.9-1ubuntu2
wpasupplicant                                                     0.6.9-3ubuntu1
x-ttcidfont-conf                                                              32
x11-apps                                                                   7.4+2
x11-common                                                        1:7.4+3ubuntu7
x11-session-utils                                                    7.3+1build1
x11-utils                                                            7.4+1build1
x11-xfs-utils                                                        7.4+1build1
x11-xkb-utils                                                              7.4+3
x11-xserver-utils                                                   7.4+2ubuntu3
x11proto-composite-dev                                                   1:0.4-2
x11proto-core-dev                                                       7.0.15-1
x11proto-damage-dev                                              1:1.1.0-2build1
x11proto-fixes-dev                                                       1:4.0-3
x11proto-input-dev                                                1.5.0-2ubuntu1
x11proto-kb-dev                                                   1.0.3-3ubuntu1
x11proto-randr-dev                                                       1.3.0-1
x11proto-render-dev                                                    2:0.9.3-2
x11proto-xext-dev                                                        7.0.4-2
x11proto-xinerama-dev                                             1.1.2-5ubuntu1
xauth                                                                  1:1.0.3-2
xbitmaps                                                          1.0.1-2ubuntu1
xcursor-themes                                                    1.0.1-5ubuntu1
xdg-user-dirs                                                      0.11-0ubuntu2
xdg-user-dirs-gtk                                                          0.8-1
xdg-utils                                                              1.0.2-6.1
xfonts-100dpi                                                    1:1.0.0-4build1
xfonts-75dpi                                                     1:1.0.0-4build1
xfonts-base                                                            1:1.0.0-6
xfonts-encodings                                                       1:1.0.2-3
xfonts-mathml                                                                  2
xfonts-scalable                                                        1:1.0.0-7
xfonts-utils                                                      1:7.4+1ubuntu1
xinit                                                                    1.1.1-1
xinput                                                                   1.4.2-1
xkb-data                                                            1.6-1ubuntu5
xml-core                                                                    0.12
xorg                                                              1:7.4+3ubuntu7
xorg-docs-core                                                           1:1.4-5
xsane                                                             0.996-2ubuntu1
xsane-common                                                      0.996-2ubuntu1
xscreensaver-data                                                  5.08-0ubuntu5
xscreensaver-gl                                                    5.08-0ubuntu5
xserver-common                                                2:1.6.4-2ubuntu4.3
xserver-xorg                                                      1:7.4+3ubuntu7
xserver-xorg-core                                             2:1.6.4-2ubuntu4.3
xserver-xorg-input-all                                            1:7.4+3ubuntu7
xserver-xorg-input-evdev                                        1:2.2.5-1ubuntu6
xserver-xorg-input-mouse                                               1:1.4.0-2
xserver-xorg-input-synaptics                                      1.1.2-1ubuntu7
xserver-xorg-input-vmmouse                                     1:12.6.4-1ubuntu3
xserver-xorg-input-wacom                                      1:0.8.4.1-0ubuntu4
xserver-xorg-video-all                                            1:7.4+3ubuntu7
xserver-xorg-video-apm                                                 1:1.2.1-2
xserver-xorg-video-ark                                                 1:0.7.1-2
xserver-xorg-video-ati                   1:6.12.99+git20090929.7968e1fb-0ubuntu1
xserver-xorg-video-chips                                               1:1.2.1-3
xserver-xorg-video-cirrus                                       1:1.3.1-1ubuntu2
xserver-xorg-video-fbdev                                               1:0.4.0-4
xserver-xorg-video-geode                                                2.11.6-1
xserver-xorg-video-i128                                                1:1.3.2-1
xserver-xorg-video-i740                                                1:1.3.0-1
xserver-xorg-video-intel                                        2:2.9.0-1ubuntu2
xserver-xorg-video-mach64                                                6.8.2-1
xserver-xorg-video-mga                                           1:1.4.11.dfsg-1
xserver-xorg-video-neomagic                                            1:1.2.3-1
xserver-xorg-video-nv                                          1:2.1.14-2ubuntu3
xserver-xorg-video-openchrome                          1:0.2.903+svn758-0ubuntu1
xserver-xorg-video-r128                                                  6.8.1-1
xserver-xorg-video-radeon                1:6.12.99+git20090929.7968e1fb-0ubuntu1
xserver-xorg-video-rendition                                           1:4.2.1-1
xserver-xorg-video-s3                                                  1:0.6.2-1
xserver-xorg-video-s3virge                                            1:1.10.2-2
xserver-xorg-video-savage                                       1:2.3.0-1ubuntu1
xserver-xorg-video-siliconmotion                                       1:1.7.2-1
xserver-xorg-video-sis                                                1:0.10.1-2
xserver-xorg-video-sisusb                                              1:0.9.1-1
xserver-xorg-video-tdfx                                                1:1.4.1-1
xserver-xorg-video-trident                                             1:1.3.1-1
xserver-xorg-video-tseng                                               1:1.2.1-1
xserver-xorg-video-v4l                                          1:0.2.0-3ubuntu1
xserver-xorg-video-vesa                                                1:2.2.1-1
xserver-xorg-video-vmware                                            1:10.16.7-1
xserver-xorg-video-voodoo                                              1:1.2.2-1
xsltproc                                                         1.1.24-2ubuntu2
xsplash                                                           0.8.4-0ubuntu1
xterm                                                               243-1ubuntu1
xtrans-dev                                                               1.2.4-1
xulrunner-1.9.1                        1.9.1.13+build1+nobinonly-0ubuntu0.9.10.1
xulrunner-1.9.1-gnome-support          1.9.1.13+build1+nobinonly-0ubuntu0.9.10.1
xulrunner-1.9.2                        1.9.2.10+build1+nobinonly-0ubuntu0.9.10.1
yelp                                                      2.28.0-0ubuntu2.9.10.1
zenity                                                           2.28.0-0ubuntu2
zip                                                                 3.0-1ubuntu1
zlib1g                                                  1:1.2.3.3.dfsg-13ubuntu3
zlib1g-dev                                              1:1.2.3.3.dfsg-13ubuntu3
```

---

