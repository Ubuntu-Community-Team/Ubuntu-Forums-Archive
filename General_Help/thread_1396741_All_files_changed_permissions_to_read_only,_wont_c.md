---
title: "All files changed permissions to read only, wont change back"
date: 2010-02-02
forum: General Help
---

### Post by typos1 on 2010-02-02
Something has changed all my file permissions to read only and when I try and change them back it wont let me. Is there something I can do i Nautilus to correct it? 

It even effects the waste basket-all the stuff in there is now read only and when I delete items I get a file operations window, which comes and then goes like its deleted them, but they re still in the waste basket, doesnt show an error message like it does if I try and move any other file.

---

### Post by Morbius1 on 2010-02-02
The very first thing that came to my mind when reading your post is how the root directory is mounted. Look at /etc/fstab. Mine looks like this:

> UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /               ext3    relatime,[COLOR=Blue]errors=remount-ro[/COLOR] 0       1The system at some given interaval will do a file check at boot. The [COLOR=Blue]errors=remount-ro [COLOR=Black]parameter will mount the partition as read only if the file system check encounters any errors. Did you get any errors the last time you booted.[/COLOR]
[/COLOR]

---

### Post by typos1 on 2010-02-02
Um, well since the upgrade to Karmic, I often have to login 20 odd times before ubuntu will start and theres that many entries for gnomepanel in system manager/processes with the processor at full tilt, have to stop them all. On going problem, though and I ve had it for  about 3 months but always been able to delete/move files. Other than that no errors.

Where is /fstab? Cant find it in homefolder

---

### Post by jamesisin on 2010-02-02
Your fstab folder is located at:

```
/etc/fstab
```

---

### Post by typos1 on 2010-02-02
Where is etc, I cant find it?

---

### Post by jamesisin on 2010-02-02
Use your terminal.  You computer has a main root for its file system (simply /).  Under that you will find a folder called etc (hence /etc).  Regardless you can view (read-only) the contents of your fstab using this command:

```
gedit /etc/fstab
```

Then copy this and past your output in between:

[NOPARSE]```
past here
```[/NOPARSE]

---

### Post by typos1 on 2010-02-02
Ok, used a terminal, but how can you get to it other than using a terminal?

Dont quite understand the last bit of your post but I get this in the terminal when I type what you said:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=********************** /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=********************** none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by jamesisin on 2010-02-02
Using the (placing your code between them) [NOPARSE]```

```[/NOPARSE] will create that cute little code box you see in my previous posts.

You can access your entire file system (beginning at /) by choosing Filesystem from Nautilus (your file browsing/exploring application).  It's located under Computer; it's located in Places.  There are many routes to get there.

Why are your UUID's listed as just asterisks?

What is the output of this command:

```
blkid
```

---

### Post by typos1 on 2010-02-02
I was looking in places, but didnt try computer, I looked in "160gb hard disc" not computer.

Very familiar with Nautilus, just not gone into "computer" before.

Now I know how to make those cute little boxes, thanks!

Thought they were ids and that it would be wise not to reveal them, was I wrong.. or paranoid? lol

Output of blkid is nothing? is that right?

---

### Post by jamesisin on 2010-02-02
> **typos1 said:**
> Thought they were ids and that it would be wise not to reveal them

There identify your drives in a manner similar to /dev/sda1 and are as benign as the /dev designations.

> Output of blkid is nothing? is that right?

I get the UUID's for both of my installation partitions.  Are you running a live CD?

---

### Post by typos1 on 2010-02-02
Not running livecd, installed Jaunty in July and upgraded to Karmic in October. I installed Jaunty from the livecd though.

---

### Post by gwpritch on 2010-02-02
The system will remount as read only on finding an error with fsck, however, it will automatically drop you into a maintainence shell so that you can fix them.

Right click on one of the files and see what the ownership of the file is. I had a similar situation where all my home files were changed to root ownership. One of the many reasons I went back to Jaunty from Karmic.

If its the same in your case try this:

```
sudo chown -R   <username>:<username> /home/<username>
```
replace <username> with your user name.
then:
```
chmod -R 774 /home/<username>  
```
this will make files in your home directory read/write/execute for owner and group and read only for all others.

---

### Post by typos1 on 2010-02-02
Ok, thanks for the reply

After putting sudo chowrn -R I get this:

user@user-desktop:~$ sudo chown -R user:user /home/user
chown: cannot access `/home/user/.gvfs': Permission denied
user@user-desktop:~$ 

After putting in chmod -R 774 /home/user nothing happens at all...

---

### Post by jamesisin on 2010-02-02
You can get your UUID's using this command:

```
sudo vol_id --uuid /dev/xxxx
```

You will want to change /dev/xxxx for each device you want to know about (such as sda1 or sdb5).  From there you just want to make sure that fstab is using the correct UUID for each device on your system.  Namely if fstab thinks your swap is on UUID=a1b2 and you see the /dev is in fact UUID=a1c4 you know there is a problem.

---

### Post by typos1 on 2010-02-02
When I type

sudo vol_id --uuid /dev/sda5


in a terminal its says command not found

How do you get past the cute little box by the way, when I hit return it just "returns" in the box and the mouse wont let me do anything past it

edit: am I supposed to find the uuid number and use that instead of the letters?

further edit: tried doing it with the uuid number and nothing happens, few spikes in the procesor usage window (have it in bottom panel) but nothing happens in the terminal and permissions are still listed as "----" in files

---

### Post by gwpritch on 2010-02-02
I really don't think that changing your UUID's in fstab is going to do anything to solve your problem. It sounds identical to the problem I had including the error with .gvfs. Unfortunately I can't remember precisely what I did to fix it other than go back to Jaunty.

Since you are familiar with nautilus do this 'very carefully'

```
gksudo nautilus /home
```

right click on your home directory and choose properties. Go to the permissions tab and post what you see in each box.

BTW are you using Karmic on a laptop?

---

### Post by jamesisin on 2010-02-03
I wasn't suggesting you change your UUID's.  I just wanted to see that they were correctly identified.  But apparently somewhere between 8.10 and 9.10 vol_id went away.  (Though the preferred method is to use UUID in fstab rather than /dev/ designations because UUID won't change.)

Also, I wonder if you might have better luck without X running.  Perhaps you can boot into a terminal and attempt to alter permissions there instead?

---

### Post by typos1 on 2010-02-03
When you say "x" do you mean xserver?-isnt that to do with nvidia/screen settings? Interaction with nvidia is rubbish on my system if I didnt have it running, the screen would be at such a low res that I cant see that bottom or top of the screen-there are only 2 settings for res without it, had similar prob when putting ubuntu on my mum's pc, although not so bad as she has nt got a widescreen monitor.

---

### Post by jamesisin on 2010-02-03
X, xserver, or the X window system is the backbone for all graphical interactions on your Linux system.  Without it, such as on the server offerings from Ubuntu, you have merely a command line and cursor.

---

### Post by typos1 on 2010-02-03
Right, I see, so its the GUI effectively?

Problem is now sorted after a couple of reboots, for most files, didnt actually DO anything. A few are still read only and everytime I change it, it changes back to"---" not even "read only", strange

---

### Post by jamesisin on 2010-02-03
It is that which allows for the GUI, so yeah.

Can you change the permissions of other files?  Like a .jpg on your desktop or something.

---

### Post by junapp on 2010-02-03
maybe post the output from 
```
history
```

---

### Post by typos1 on 2010-02-04
Yeah, I can change permissions of other things.

Output og history is: (Hope this is ok, its very long! Take it it goes back to July when I first installed)

```
-desktop:~$ history
    1  sudo apt-get install multisync-tools opensync-plugin-synce synce-sync-engine
    2  sudo apt-get install opensync-plugin-evolution
    3  sudo apt-get install synce-hal librra-tools librapi2-tools
    4  sudo apt-key adv --recv-keys --keyserver subkeys.pgp.net 7D2C7A23BF810CD5
    5  synce-pls
    6  ./configure
    7  ./configure synce
    8  ./configure synce-gnomevfs-0.13 
    9  sudo mv ~/Desktop/jre-6u13-linux-x64.bin /opt/java/64
   10  cd java
   11  sudo mkdir 32 64
   12  sudo mv ~/Desktop/jre-6u13-linux-x64.bin /opt/java/64
   13  sudo chmod 755 /opt/java/64/jre-6u13-linux-x64.bincd /opt
   14  sudo mkdir java
   15  cd java
   16  sudo mkdir 32 64sudo mv ~/Desktop/jre-6u13-linux-x64.bin /opt/java/64
   17  sudo chmod 755 /opt/java/64/jre-6u13-linux-x64.bin
   18  cd /opt/java/64
   19  sudo ./jre-6u13-linux-x64.bin
   20  sudo apt-get installjre-6u13-linux-x64.bin
   21  jre-6u13-linux-x64.bin
   22  sudo apt -get install jre-6u13-linux-x64.b
   23  sudo apt get-install jre-6u13-linux-x64.bin
   24  sudo gedit /etc/X11/xorg.conf
   25  /etc/smart/channels/rudd-o.channel
   26  /etc/smart/channels/rudd-o.channel[rudd-o]
   27  name=The missing RPMs
   28  baseurl=http://yum.rudd-o.com/
   29  sudo apt-get install realplayer
   30  sudo apt get mplayer
   31  sudo apt- get mplayer
   32  sudo apt-get mplayer
   33  sudo apt-get mozilla mplayer
   34  sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
   35  sudo apt-get install flashplugin-nonfree
   36  ubuntu-restricted-extras
   37  sudo apt-get install flashplugin-nonfree
   38  sudo apt-get realplayer
   39  sudo apt-get instal realplayer
   40  sudo apt-get install realplayer
   41  sudo apt-get install libflashplaer
   42  sudo apt-get install libflashplayer
   43  sudo apt-get install libflashplayer_x86_64
   44  sudo dpkg-reconfigure -phigh xserver-xorg
   45  nvidia xconfig
   46  nvidia-xconfig
   47  sudo nvidia-xconfig
   48  sudo dpkg-reconfigure -phigh xserver-xorg
   49  xrandr
   50  xrandr -s 1680x1050
   51  xrandr
   52  sudo apt-get remove nvidia*
   53  sudo dpkg-reconfigure -phigh xserver-xorg
   54  xrandr
   55  sudo apt-get nvidia-xconfig
   56  sudo apt-get nvidia
   57  sudo apt-get install nvidia
   58  sudo dpkg-reconfigure -phigh xserver-xorg
   59  sudo nvidia-xconfig
   60  sudo ln -s /usr/lib/flashplugin-nonfree/libflashplayer.so
   61  sudo nvidia-xconfig
   62  sudo mv libflashplayer.so /usr/lib/mozila/plugins
   63  sudo apt-get update
   64  sudo apt-get install medibuntu-keyring
   65  sudo apt-get install nvidia-96-modaliases nvidia-71-modaliases nvidia-180-modaliases nvidia-173-modaliases
   66  xrandr
   67  sudo mv libflashplayer.so /usr/lib/mozila/plugins
   68  `libflashplayer.so' to `/usr/lib/mozilla/plugins
   69  sudo mv libflashplayer.so /usr/lib/mozilla/plugins
   70  sudo apt-get install flashplugin-nonfree
   71  sudo apt-install flashplugin-nonfree
   72  sudo apt-get flashplayer
   73  sudo apt-get install flashplugin-nonfree
   74  sudo updatedb
   75  and
   76  locate libflashplayer.sosudo updatedb
   77  sudo updatedb
   78  locate libflashplayer.so
   79  sudo updatedb
   80  gksudo nvidia-settings 
   81  gksudo nvidia-settings set resolution and save
   82  nvidia-settings
   83  gksudo nvidia-settings
   84  sudo apt-get install amsn plugins
   85  search amsn plugins
   86  search-get amsn plugins
   87  sudo apt-get installamsnplugins
   88  gksudo nvidia-settings 
   89  sudo apt-get install synce-hal librra-tools librapi2-tools
   90  sudo apt-get install multisync-tools opensync-plugin-synce synce-sync-engine
   91  y
   92  sudo apt-get install opensync-plugin-evolution
   93  msynctool --sync synce-sync
   94  msynctool --addmember synce-sync evo2-sync
   95  sudo apt-get synce-gnome
   96  sudo apt-gert synce-gnome aplet
   97  sudo apt-get instal synce-gnome applet
   98  sudo apt-get install synce-gnome applet
   99  sudo apt-get install ubuntu-restricted-extras
  100  sudo apt-get install nspluginwrapper
  101  sudo apt-get install  alsa-plugins-pulseaudio.x86_64
  102  sudo apt-get install libcurl.x86_64 
  103  sudo find /usr/lib64/mozilla/plugins
  104  sudo find /usr/lib32/mozilla/plugins
  105  sudo find nspluginwrapper
  106  sudo apt-get install libflashplayer.so
  107  sudo find npwrapper.libflashplayer.so
  108  sudo apt-get install libflashplayer.so
  109  synce-pls
  110  Directory               2008-01-01 11:00:18  My Pictures/
  111  Directory               2008-01-01 11:00:20  Templates/
  112  Directory               2008-01-01 11:00:20  Personal/
  113  Directory               2008-01-01 11:00:20  Business/
  114  Directory               2008-01-01 11:00:20  My Music/
  115  Directory               2008-01-01 11:00:20  My Ringtones/
  116  Directory               2009-02-13 21:30:28  My Videos/
  117  Directory               2009-02-13 21:30:28  DCIM/
  118  Archive          34084  2009-05-21 16:24:12  ScanTool.log
  119  Directory               2009-03-10 22:10:54  Dictionaries/
  120  Directory               2009-05-28 21:37:10  Podcasts/
  121  Directory               2009-05-28 21:38:12  RSS Reader/
  122  Normal           16054  2009-06-03 22:55:56  0_0.amr
  123  synce-pls
  124  metacity --replace
  125  compiz --replace
  126  metacity --replace&
  127  meatcity --replace&
  128  metacity --replace&
  129  ipconfig /all
  130  ipconfig
  131  sudo gedit /etc/apt/sources.list
  132  tar xzf zcs.tgz
  133  $ cp /home/tom/Desktop/thunderbird-2.0.0.0.tar.gz .
  134  $ tar -zxvf thunderbird-2.0.0.0.tar.gz$ cp /home/jason/Desktop/thunderbird-2.0.0.0.tar.gz .
  135  $ tar -zxvf thunderbird-2.0.0.0.tar.gz# cd /opt
  136  # mkdir thunderbird
  137  # cd thunderbird
  138  # cp /home/tom/Desktop/thunderbird-2.0.0.0.tar.gz .
  139  # tar -zxvf thunderbird-2.0.0.0.tar.gz
  140  $ /opt/thunderbird/thunderbird &
  141  $ cp /home/jason/Desktop/thunderbird-2.0.0.0.tar.gz .
  142  $ tar -zxvf thunderbird-2.0.0.0.tar.gz$ cd thunderbird
  143  $ ./thunderbird$ sudo apt-get update
  144  $ sudo apt-get install thunderbird
  145  $ sudo apt-get update
  146  $ sudo apt-get install thunderbird
  147  sudo apt - get install thunderbird
  148  sudo apt-get update
  149  $ sudo apt-get install thunderbird
  150  apt - get update
  151  sudo apt - get install thunderbird
  152  sudo apt-get installl thunderbird
  153  sudo apt-get install thunderbird
  154  sudo apt get:libflashplayer.so
  155  '/home/jason/Desktop/libflashplayer.so' 
  156  sudo mkdir /usr/lib/mozilla/plugins
  157  '/home/jason/Desktop/libflashplayer.so ' 
  158  ./flashplayer-installer
  159  sudo apt get-libflasplayer.so
  160  sudo apt get:libflashplashplayer.so
  161  aplay -l
  162  lspci -v
  163  user@machine:~$ asoundconf list
  164  Names of available sound cards:
  165  SB
  166  HDMI
  167  T71Universe
  168  user@machine:~$ asoundconf set-default-card T71Universe
  169  alsamixer
  170  sudo apt-get install alsa-oss
  171  asoundconf set-default-card nVidia Corporation MCP61
  172  asoundconf set-default-card nVidia MCP61
  173  asoundconf list
  174  asoundconf-set-default-card NVidia
  175  asoundconf set-default-card NVidia
  176  asoundconf set-default-card Device
  177  alsamixer
  178  sudo getlibs ./AdobeAIRInstaller.bin
  179  $ sudo getlibs -l libgnome-keyring.so
  180  $ sudo getlibs -l libgnome-keyring.so.0
  181  $ sudo getlibs -l libgnome-keyring.so.0.1.1
  182  sudo getlibs ./AdobeAIRInstaller.bin
  183  $ sudo getlibs ./AdobeAIRInstaller.bin
  184  sudo getlibs ./AdobeAIRInstaller.bin
  185  '/home/jason/Desktop/AdobeAIRInstaller.bin' man getlibs
  186  sudo getlibs
  187  sudo getlibs ./AdobeAIRInstaller.bin
  188  $ sudo getlibs -l libgnome-keyring.so
  189  $ sudo getlibs -l libgnome-keyring.so.0
  190  $ sudo getlibs -l libgnome-keyring.so.0.1.1
  191  sudo getlibs ./AdobeAIRInstaller.bin
  192  sudo getlibs AdobeAIRInstaller.bin
  193  sudo getlibs jason-desktop/AdobeAIRInstaller.bin
  194  sudo getlibs ./AdobeAIRInstaller.bin
  195  sudo getlibs desktop/AdobeAIRInstaller.bin
  196  sudo getlibs ./AdobeAIRInstaller.bin
  197  sudo getlibs jason/AdobeAIRInstaller.bin
  198  sudo getlibs -l libgnome-keyring.so
  199  $ sudo getlibs -l libgnome-keyring.so
  200  $ sudo getlibs -l libgnome-keyring.so.0
  201  $ sudo getlibs -l libgnome-keyring.so.0.1.1
  202  y
  203  sudo getlibs ./AdobeAIRInstaller.bin
  204  sudo apt getlib ./AdobeAIRInstaller.bin
  205  sudo aptitude install alsa-oss
  206  sudp gedit/etc/firefoxrc
  207  sudo gedit/etc/firefox/firefoxrc
  208  sudo gedit /etc/firefox/firefoxrc
  209  sudo ./AdobeAIRInstaller.bin
  210  sudo apt-get install ia32-libs
  211  sudo getlibs -l libgnome-keyring.so
  212  sudo getlibs -l libgnome-keyring.so.0
  213  sudo getlibs -l libgnome-keyring.so.0.1.1
  214  sudo getlibs -l libgnome-keyring.so
  215  sudo cp /usr/lib/libadobecertstore.so /usr/lib32
  216  $ sudo getlibs ./AdobeAIRInstaller.bin
  217  $ sudo file-roller ./libnss3-1d_3.12.0~beta3-0ubuntu1_i386.deb
  218  sudo file-roller ./libnss3-1d_3.12.0~beta3-0ubuntu1_i386.deb
  219  $ sudo apt-get install lib32nss-mdns
  220  sudo apt-get install lib32nss-mdns
  221  sudo cp /usr/lib/libadobecertstore.so /usr/lib32
  222  sudo getlibs ./AdobeAIRInstaller.bin
  223  sudo ln -s /usr/lib32/libnss3.so.1d /usr/lib32/libnss3.so
  224  sudo ln -s /usr/lib32/libssl3.so.1d /usr/lib32/libssl3.so
  225  sudo ln -s /usr/lib32/libnspr4.so.0d /usr/lib32/libnspr4.so
  226  /AdobeAIRIntaller.bin
  227  sudo getlibs ./AdobeAIRInstaller.bin
  228  sudo getlibs jason/desktop/Adobe/AIRInstaller.bin
  229  sudo getlibs desktop/AdobeAIRInsstaller.bin
  230  /opt'/'BBC iPlayer Desktop'/bin/'BBC iPlayer Desktop'
  231  udo file-roller ./libnss3-1d_3.12.0~beta3-0ubuntu1_i386.deb
  232  sudo file-roller ./libnss3-1d_3.12.0~beta3-0ubuntu1_i386.deb
  233  ./thunderbird -ProfileManager
  234  path/to/application -profilemanager
  235  ./thunderbird -profilemanager
  236  path/to/thunderbird -profilemanager
  237  ~/.mozilla-thunderbird -Profilemanager
  238  find thunderbird profile manager
  239  findmozilla-thunderbird profilemanager
  240  find mozilla-thunderbird profilemanager
  241  ifconfig eth0
  242  sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
  243  sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
  244  sudo apt-get install libdvdcss2
  245  sudo apt-get install w64codecs
  246  sudo apt-get install libxine1-ffmpeg
  247  gksudo nvidia-settings
  248  alsa mixer
  249  alsamixer
  250  gedit /etc/fstab
  251  sudo chown -R jason:jason/home/jason
  252  sudo chown -R jason:jason /home/jason
  253  chmod -R 774 /home/jason
  254  sudo vol_id --uuid /dev/jsaon
  255  sudo vol_id --uuid /dev/jason
  256  sudo vol_id --uuid /dev/sda5
  257  sudo vol_id --uuid /dev/sda5 /
  258  gedit /etc/fstab
  259  sudo vol_id --77cc004c-3461-41dd-8e77-3b3340dfe043/dev/sda5
  260  history

```

---

