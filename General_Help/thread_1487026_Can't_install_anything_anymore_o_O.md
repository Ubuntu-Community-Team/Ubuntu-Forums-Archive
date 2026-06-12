---
title: "Can't install anything anymore o_O"
date: 2010-05-18
forum: General Help
---

### Post by teddu379 on 2010-05-18
Hello,
I was trying to install PlayOnLinux but it froze at about 85% after it downloaded via the Software Center. So I had to shut the Software Center. The PlayOnLinux did install despite the fact it froze at 85%. I can't install any more stuff bec the Software Center seems opened all time some how and I get the "You have to repair this before you can install or remove any further software." error.

I tried the "sudo dpkg --configure -a" command it gives me this, looks like it's stuck at some connection. I'm pretty new to Linux.




```
Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/trebuc32.exe?download&failedmirror=internode.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/trebuc32.exe?download&failedmirror=internode.dl.sourceforge.net) [following]
--2010-05-18 21:20:15--  [http://downloads.sourceforge.net/sourceforge/corefonts/trebuc32.exe?download&failedmirror=internode.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/trebuc32.exe?download&failedmirror=internode.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe) [following]
--2010-05-18 21:20:16--  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe)
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

--2010-05-18 21:20:37--  [http://voxel.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe](http://voxel.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe)
Resolving voxel.dl.sourceforge.net... 208.122.31.4, 208.122.31.12, 208.122.31.11, ...
Connecting to voxel.dl.sourceforge.net|208.122.31.4|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/trebuc32.exe?download&failedmirror=voxel.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/trebuc32.exe?download&failedmirror=voxel.dl.sourceforge.net) [following]
--2010-05-18 21:20:38--  [http://downloads.sourceforge.net/sourceforge/corefonts/trebuc32.exe?download&failedmirror=voxel.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/trebuc32.exe?download&failedmirror=voxel.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe) [following]
--2010-05-18 21:20:39--  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe)
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

--2010-05-18 21:21:00--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe)
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/trebuc32.exe?download&failedmirror=kent.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/trebuc32.exe?download&failedmirror=kent.dl.sourceforge.net) [following]
--2010-05-18 21:21:00--  [http://downloads.sourceforge.net/sourceforge/corefonts/trebuc32.exe?download&failedmirror=kent.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/trebuc32.exe?download&failedmirror=kent.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe) [following]
--2010-05-18 21:21:02--  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe)
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

--2010-05-18 21:21:23--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe)
Resolving internap.dl.sourceforge.net... 69.88.152.3
Connecting to internap.dl.sourceforge.net|69.88.152.3|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://prdownloads.sourceforge.net/corefonts/trebuc32.exe?download&failedmirror=internap.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/trebuc32.exe?download&failedmirror=internap.dl.sourceforge.net) [following]
--2010-05-18 21:21:25--  [http://prdownloads.sourceforge.net/corefonts/trebuc32.exe?download&failedmirror=internap.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/trebuc32.exe?download&failedmirror=internap.dl.sourceforge.net)
Resolving prdownloads.sourceforge.net... 216.34.181.59
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe) [following]
--2010-05-18 21:21:26--  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe)
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

--2010-05-18 21:21:47--  [http://downloads.sourceforge.net/corefonts/verdan32.exe](http://downloads.sourceforge.net/corefonts/verdan32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe) [following]
--2010-05-18 21:21:47--  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe)
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

--2010-05-18 21:22:08--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
Resolving switch.dl.sourceforge.net... 32.1.6.32
Connecting to switch.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out.
Giving up.

--2010-05-18 21:22:29--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=mesh.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=mesh.dl.sourceforge.net) [following]
--2010-05-18 21:22:30--  [http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=mesh.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=mesh.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe) [following]
--2010-05-18 21:22:30--  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe)
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

--2010-05-18 21:22:51--  [http://dfn.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://dfn.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
Resolving dfn.dl.sourceforge.net... 194.95.236.130
Connecting to dfn.dl.sourceforge.net|194.95.236.130|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=dfn.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=dfn.dl.sourceforge.net) [following]
--2010-05-18 21:22:52--  [http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=dfn.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=dfn.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe) [following]
--2010-05-18 21:22:53--  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe)
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

--2010-05-18 21:23:14--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
Resolving heanet.dl.sourceforge.net... 32.1.7.112
Connecting to heanet.dl.sourceforge.net|32.1.7.112|:80... failed: Connection timed out.
Giving up.

--2010-05-18 21:23:35--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
Resolving jaist.dl.sourceforge.net... 150.65.7.130
Connecting to jaist.dl.sourceforge.net|150.65.7.130|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=jaist.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=jaist.dl.sourceforge.net) [following]
--2010-05-18 21:23:36--  [http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=jaist.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=jaist.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe) [following]
--2010-05-18 21:23:37--  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe)
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

--2010-05-18 21:23:58--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
Resolving nchc.dl.sourceforge.net... 32.1.14.16
Connecting to nchc.dl.sourceforge.net|32.1.14.16|:80... failed: Connection timed out.
Giving up.

--2010-05-18 21:24:19--  [http://ufpr.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://ufpr.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
Resolving ufpr.dl.sourceforge.net... 200.17.202.1
Connecting to ufpr.dl.sourceforge.net|200.17.202.1|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=ufpr.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=ufpr.dl.sourceforge.net) [following]
--2010-05-18 21:24:20--  [http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=ufpr.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=ufpr.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe) [following]
--2010-05-18 21:24:22--  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe)
Resolving garr.dl.sourceforge.net... 32.1.7.96, 2001:760:ffff:b0::34
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
--2010-05-18 21:24:44--  [http://internode.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://internode.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
Resolving internode.dl.sourceforge.net... 150.101.135.12
Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=internode.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=internode.dl.sourceforge.net) [following]
--2010-05-18 21:24:45--  [http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=internode.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=internode.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe) [following]
--2010-05-18 21:24:45--  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe)
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

--2010-05-18 21:25:06--  [http://voxel.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://voxel.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
Resolving voxel.dl.sourceforge.net... 208.122.31.4
Connecting to voxel.dl.sourceforge.net|208.122.31.4|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=voxel.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=voxel.dl.sourceforge.net) [following]
--2010-05-18 21:25:07--  [http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=voxel.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=voxel.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe) [following]
--2010-05-18 21:25:07--  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe)
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

--2010-05-18 21:25:28--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=kent.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=kent.dl.sourceforge.net) [following]
--2010-05-18 21:25:28--  [http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=kent.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=kent.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe) [following]
--2010-05-18 21:25:29--  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe)
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

--2010-05-18 21:25:50--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
Resolving internap.dl.sourceforge.net... 69.88.152.3
Connecting to internap.dl.sourceforge.net|69.88.152.3|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://prdownloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=internap.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=internap.dl.sourceforge.net) [following]
--2010-05-18 21:25:51--  [http://prdownloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=internap.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=internap.dl.sourceforge.net)
Resolving prdownloads.sourceforge.net... 216.34.181.59
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe) [following]
--2010-05-18 21:25:52--  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe)
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

--2010-05-18 21:26:13--  [http://downloads.sourceforge.net/corefonts/webdin32.exe](http://downloads.sourceforge.net/corefonts/webdin32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe) [following]
--2010-05-18 21:26:13--  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe)
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

--2010-05-18 21:26:34--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe)
Resolving switch.dl.sourceforge.net... 32.1.6.32, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out.
Connecting to switch.dl.sourceforge.net|2001:620:0:1b::21|:80... failed: Network is unreachable.
--2010-05-18 21:26:55--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe)
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=mesh.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=mesh.dl.sourceforge.net) [following]
--2010-05-18 21:26:57--  [http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=mesh.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=mesh.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe) [following]
--2010-05-18 21:26:58--  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe)
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

--2010-05-18 21:27:19--  [http://dfn.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe](http://dfn.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe)
Resolving dfn.dl.sourceforge.net... 194.95.236.130
Connecting to dfn.dl.sourceforge.net|194.95.236.130|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=dfn.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=dfn.dl.sourceforge.net) [following]
--2010-05-18 21:27:20--  [http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=dfn.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=dfn.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe) [following]
--2010-05-18 21:27:21--  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe)
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

--2010-05-18 21:27:42--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe)
Resolving heanet.dl.sourceforge.net... 32.1.7.112, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|32.1.7.112|:80... failed: Connection timed out.
Connecting to heanet.dl.sourceforge.net|2001:770:18:aa40::c101:c142|:80... failed: Network is unreachable.
--2010-05-18 21:28:03--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe)
Resolving jaist.dl.sourceforge.net... 150.65.7.130
Connecting to jaist.dl.sourceforge.net|150.65.7.130|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=jaist.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=jaist.dl.sourceforge.net) [following]
--2010-05-18 21:28:03--  [http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=jaist.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=jaist.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe) [following]
--2010-05-18 21:28:04--  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe)
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

--2010-05-18 21:28:25--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe)
Resolving nchc.dl.sourceforge.net... 32.1.14.16, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|32.1.14.16|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2010-05-18 21:28:46--  [http://ufpr.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe](http://ufpr.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe)
Resolving ufpr.dl.sourceforge.net... 200.17.202.1, 200.236.31.1
Connecting to ufpr.dl.sourceforge.net|200.17.202.1|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=ufpr.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=ufpr.dl.sourceforge.net) [following]
--2010-05-18 21:28:49--  [http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=ufpr.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=ufpr.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe) [following]
--2010-05-18 21:28:50--  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe)
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

--2010-05-18 21:29:11--  [http://internode.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe](http://internode.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe)
Resolving internode.dl.sourceforge.net... 150.101.135.12
Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=internode.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=internode.dl.sourceforge.net) [following]
--2010-05-18 21:29:12--  [http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=internode.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=internode.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe) [following]
--2010-05-18 21:29:12--  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe)
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

--2010-05-18 21:29:33--  [http://voxel.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe](http://voxel.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe)
Resolving voxel.dl.sourceforge.net... 208.122.31.12, 208.122.31.18, 208.122.31.4, ...
Connecting to voxel.dl.sourceforge.net|208.122.31.12|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=voxel.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=voxel.dl.sourceforge.net) [following]
--2010-05-18 21:29:35--  [http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=voxel.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=voxel.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe) [following]
--2010-05-18 21:29:38--  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe)
Resolving garr.dl.sourceforge.net... 32.1.7.96, 2001:760:ffff:b0::34
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Connecting to garr.dl.sourceforge.net|2001:760:ffff:b0::34|:80... failed: Network is unreachable.
--2010-05-18 21:30:00--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe)
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=kent.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=kent.dl.sourceforge.net) [following]
--2010-05-18 21:30:01--  [http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=kent.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=kent.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe) [following]
--2010-05-18 21:30:02--  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe)
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

--2010-05-18 21:30:23--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe)
Resolving internap.dl.sourceforge.net... 69.88.152.3
Connecting to internap.dl.sourceforge.net|69.88.152.3|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://prdownloads.sourceforge.net/corefonts/webdin32.exe?download&failedmirror=internap.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/webdin32.exe?download&failedmirror=internap.dl.sourceforge.net) [following]
--2010-05-18 21:30:24--  [http://prdownloads.sourceforge.net/corefonts/webdin32.exe?download&failedmirror=internap.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/webdin32.exe?download&failedmirror=internap.dl.sourceforge.net)
Resolving prdownloads.sourceforge.net... 216.34.181.59
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe) [following]
--2010-05-18 21:30:25--  [http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://garr.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe)
Resolving garr.dl.sourceforge.net... 32.1.7.96
Connecting to garr.dl.sourceforge.net|32.1.7.96|:80... failed: Connection timed out.
Giving up.

The following fonts failed to install :  andale32.exe arialb32.exe arial32.exe comic32.exe courie32.exe georgi32.exe impact32.exe times32.exe trebuc32.exe verdan32.exe webdin32.exe.
The fonts are NOT installed.
Please run 'dpkg-reconfigure ttf-mscorefonts-installer' to perform the installation again

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Setting up python-wxversion (2.8.10.1-0ubuntu1) ...

Processing triggers for python-central ...
Setting up python-wxgtk2.8 (2.8.10.1-0ubuntu1) ...
update-alternatives: using /usr/lib/wx/python/wx2.8.pth to provide /usr/lib/python2.5/site-packages/wx.pth (wx2.5.pth) in auto mode.
update-alternatives: using /usr/lib/wx/python/wx2.8.pth to provide /usr/lib/python2.6/dist-packages/wx.pth (wx2.6.pth) in auto mode.

Processing triggers for python-central ...
Setting up playonlinux (3.7.3-1) ...
```

---

### Post by teddu379 on 2010-05-18
nvm, while I was typing my post it finished and it got fixed. It was just taking forever to execute the command or something.
Mods can delete my post. Thanks ^^

---

### Post by Sef on 2010-05-18
> nvm, while I was typing my post it finished and it got fixed. It was  just taking forever to execute the command or something.
Mods can delete my post. Thanks ^^

1) Happy to hear that it got done.

2) Posts are not deleted, but I will locked it.

---

