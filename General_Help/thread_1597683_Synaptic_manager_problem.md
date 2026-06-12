---
title: "Synaptic manager problem"
date: 2010-10-15
forum: General Help
---

### Post by shanks. on 2010-10-15
last time i used terminal , it was irresponsive, so i closed it manually

and now when i restart the comp and try to use synaptic manager , i get the message:

```
An error occurred

The following details are provided:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

E: _cache->open() failed, please report.

```any help please?

even update manager is not working, it says software index is broken :(

---

### Post by shanks. on 2010-10-15
when i use the command 

sudo dpkg --configure -a, my output is as follows:

```
sudo dpkg --configure -a
Setting up ttf-mscorefonts-installer (3.2) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2010-10-16 00:37:27--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... failed: Connection timed out.
Giving up.

--2010-10-16 00:37:58--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80...
```

---

### Post by Toz on 2010-10-15
You probably interrupted an update or installation that was running in the terminal. 'sudo dpkg --configure -a' is the proper way to fix this, but you don't seem to be connecting to switch.dl.sourceforge.net|130.59.138.21|:80. Are you having a network problem? Is your connection to the internet still active? Perhaps there was a problem with sourceforge. Try it again.

---

### Post by shanks. on 2010-10-15
ya my internet connection is fine

i live in my college campus  and internet is quite restricted over here


but ya internet is working although  and till now this is what i have been getting

```
sudo dpkg --configure -a
Setting up ttf-mscorefonts-installer (3.2) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2010-10-16 00:39:28--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... failed: Connection timed out.
Giving up.

--2010-10-16 00:39:49--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... failed: Connection timed out.
Connecting to switch.dl.sourceforge.net|2001:620:0:1b::21|:80... failed: Network is unreachable.
--2010-10-16 00:40:10--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... failed: Connection timed out.
Giving up.

--2010-10-16 00:40:42--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving dfn.dl.sourceforge.net... 194.95.236.130
Connecting to dfn.dl.sourceforge.net|194.95.236.130|:80... failed: Connection timed out.
Giving up.

--2010-10-16 00:41:24--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving heanet.dl.sourceforge.net... 193.1.193.66, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... failed: Connection timed out.
Connecting to heanet.dl.sourceforge.net|2001:770:18:aa40::c101:c142|:80... failed: Network is unreachable.
--2010-10-16 00:41:46--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving jaist.dl.sourceforge.net... 150.65.7.130, 2001:200:141:feed::feed
Connecting to jaist.dl.sourceforge.net|150.65.7.130|:80... failed: Connection timed out.
Connecting to jaist.dl.sourceforge.net|2001:200:141:feed::feed|:80... failed: Network is unreachable.
--2010-10-16 00:42:08--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2010-10-16 00:42:29--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving ufpr.dl.sourceforge.net... 200.17.202.1
Connecting to ufpr.dl.sourceforge.net|200.17.202.1|:80... failed: Connection timed out.
Giving up.

--2010-10-16 00:42:53--  http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internode.dl.sourceforge.net... 150.101.135.12
Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... failed: Connection timed out.
Giving up.

--2010-10-16 00:43:35--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving voxel.dl.sourceforge.net... 208.122.31.24, 208.122.31.26, 208.122.31.27, ...
Connecting to voxel.dl.sourceforge.net|208.122.31.24|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|208.122.31.26|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|208.122.31.27|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|208.122.31.28|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|208.122.31.29|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|208.122.31.3|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|208.122.31.4|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|208.122.31.11|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|208.122.31.12|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|208.122.31.13|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|208.122.31.14|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|208.122.31.15|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|208.122.31.16|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|208.122.31.17|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|208.122.31.18|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|208.122.31.22|:80... failed: Connection timed out.
Giving up.

--2010-10-16 00:49:25--  http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... failed: Connection timed out.
Giving up.

--2010-10-16 00:49:57--  http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internap.dl.sourceforge.net... 69.88.152.3
Connecting to internap.dl.sourceforge.net|69.88.152.3|:80... failed: Connection timed out.
Giving up.

--2010-10-16 00:50:24--  http://downloads.sourceforge.net/corefonts/arialb32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... failed: Connection timed out.
Giving up.

--2010-10-16 00:50:45--  http://switch.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe
Resolving switch.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... failed: Connection timed out.
Connecting to switch.dl.sourceforge.net|2001:620:0:1b::21|:80... failed: Network is unreachable.
--2010-10-16 00:51:06--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... failed: Connection timed out.
Giving up.

--2010-10-16 00:51:27--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe
Resolving dfn.dl.sourceforge.net... 194.95.236.130
Connecting to dfn.dl.sourceforge.net|194.95.236.130|:80... failed: Connection timed out.
Giving up.

--2010-10-16 00:52:08--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe
Resolving heanet.dl.sourceforge.net... 193.1.193.66, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... failed: Connection timed out.
Connecting to heanet.dl.sourceforge.net|2001:770:18:aa40::c101:c142|:80... failed: Network is unreachable.
--2010-10-16 00:52:30--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe
Resolving jaist.dl.sourceforge.net... 150.65.7.130, 2001:200:141:feed::feed
Connecting to jaist.dl.sourceforge.net|150.65.7.130|:80... failed: Connection timed out.
Connecting to jaist.dl.sourceforge.net|2001:200:141:feed::feed|:80... failed: Network is unreachable.
--2010-10-16 00:52:51--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2010-10-16 00:53:12--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe
Resolving ufpr.dl.sourceforge.net... 200.17.202.1
Connecting to ufpr.dl.sourceforge.net|200.17.202.1|:80... failed: Connection timed out.
Giving up.

--2010-10-16 00:53:53--  http://internode.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe
Resolving internode.dl.sourceforge.net... 150.101.135.12
Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... failed: Connection timed out.
Giving up.

--2010-10-16 00:54:14--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe
Resolving voxel.dl.sourceforge.net... 208.122.31.12, 208.122.31.13, 208.122.31.14, ...
Connecting to voxel.dl.sourceforge.net|208.122.31.12|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|208.122.31.13|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|208.122.31.14|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|208.122.31.15|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|208.122.31.16|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|208.122.31.17|:80... 

```

---

### Post by Toz on 2010-10-15
Well, it's not connecting:

"Connecting to voxel.dl.sourceforge.net|208.122.31.16|:80... **failed: Connection timed out.**"

Can you browse the internet with this computer? Do you have a proxy that you need to go through?

---

### Post by shanks. on 2010-10-15
> **Toz said:**
> Well, it's not connecting:

"Connecting to voxel.dl.sourceforge.net|208.122.31.16|:80... **failed: Connection timed out.**"

Can you browse the internet with this computer? Do you have a proxy that you need to go through?


well i can very well browse the internet with this comp with a proxy on

everything works fine except that connection to sourceforge :(

---

### Post by Quackers on 2010-10-15
Sourceforge isn't down here. I've just connected ok. Can you connect to it in your browser?

---

### Post by bashphoenux on 2010-10-16
looks like there is a problem with your internet !
try restarting your modem and try again !

---

### Post by 3rdalbum on 2010-10-16
> **shanks. said:**
> well i can very well browse the internet with this comp with a proxy on

Wget needs to be told about your proxy - can anyone advise the op how to set this up?

---

### Post by sunnn on 2010-10-16
I too hv simillar problem...

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 1 in source list /etc/apt/sources.list (absolute dist), E:Type 'ain' is not known on line 1 in source list /etc/apt/sources.list.d/bean123ch-burg-lucid.list, E:The list of sources could not be read.'

---

### Post by lisati on 2010-10-16
> **sunnn said:**
> I too hv simillar problem...

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 1 in source list /etc/apt/sources.list (absolute dist), E:Type 'ain' is not known on line 1 in source list /etc/apt/sources.list.d/bean123ch-burg-lucid.list, E:The list of sources could not be read.'
@Sunnn: yours is a different problem. It might be a good idea to start your own thread after checking the forum for a solution. And please use the default font size in your posts.

---

### Post by Toz on 2010-10-16
You need to know your proxy information....

1. Open up a terminal window
2. Type > sudo bash  and enter your password
3. Type > http_proxy="http://<your_proxy_info_here>"
4. > dpkg --configure -a

---

### Post by Toz on 2010-10-16
@Sunn: There is a typo in your /etc/apt/sources.list.d/bean123ch-burg-lucid.list file.

---

### Post by shanks. on 2010-12-04
toz u were right , i had searched in net and found the same oslution.. thanks anyways

---

### Post by ImLi4m on 2010-12-16
Please could you post your fix shanks. as I am having similar problems.

---

