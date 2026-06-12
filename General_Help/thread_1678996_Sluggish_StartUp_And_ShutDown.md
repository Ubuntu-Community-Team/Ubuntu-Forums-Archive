---
title: "Sluggish StartUp And ShutDown"
date: 2011-01-31
forum: General Help
---

### Post by ChipOManiac on 2011-01-31
Hello There!

First Of All, Many Thanks To AnyOne Who Took The Time To Read This... I Really Appreciate It... :KS

I'm Running Kubuntu Lucid LTS And For The Past Few Months And I've Noticed That The StartUp And ShutDown Times Are Very Long (Even Longer Than Before Usually 6 - 7 Minutes)... The General BootUp Procedure Is The Same Time Though. Only When I Log Onto KDE Does This Happen. I Can't Really UnderStand What's Slowing It So Down.

A Small Thing I Notiiced Is That When KDE's Logging On There's This Transparent Like Box In The Left-Top Corner With A Shadow That Constantly Flickers In Opacity (Boy That Sounds Stupid) (I'm Assuming That It's Got SomeThing To Do With KDE-GTK... Or WhatEver :rolleyes:) Does That Have Any Significance? 

Added To This There's High Disk Usage During Both StartUp And ShutDown. (I Do Have A Lot Of Files But I Don't Think There Are So Many That It Gives A Situation Like This Since It Never Happened Before).

My Specifications:
COMPAQ Presario C500 WideScreen
Intel Pentium Dual-Core
System Memory : 1015 MiB
HDD : 117 GiB

All Help (And Criticism ;)) Is Appreciated...

(Just Asking: How Many Times  And How Frequently Can You Do UnClean ShutDowns Before The Disk Is In Danger Of BadBlocks?)

Thank You Very Much...

---

### Post by gordintoronto on 2011-01-31
How much free space do you have in each partition? (Disk usage analyzer will tell you, but I don't remember whether it is installed by default.)

---

### Post by ChipOManiac on 2011-02-01
Thank You For Taking The Time.

The Disk Is 117 GiB, And My Root Partition Usage Is 74.18 GiB Out Of 108.95 GiB... Is This The Cause? :(. I've Run badblocks And fsck While On A Live CD To See It It's A Problem With The Disk... But No Problems At All...

Thank You For The Help AnyWay :D

---

### Post by gordintoronto on 2011-02-01
Sorry, I haven't helped at all. You have 34 GB free, which is completely reasonable.

I'm not familiar with KDE. Do you know if it has a "disk check" program?

One of the most common causes of boot-up grief is the video card. What one do you have? (command lspci will show it, on the line which includes "VGA".) Usually that grief is a complete failure to boot up, not a delay.

---

### Post by ChipOManiac on 2011-02-04
> Sorry, I haven't helped at all. You have 34 GB free, which is completely reasonable.Well This Is Help Enough :D

Here's The OutPut From "lspci":
[FONT=Courier New]00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)[/FONT]

Not Sure If KDE Has A Disk Checker But I'll See... Thanks For The Reply... Will Post As Soon As I Get SomeThing... :D

---

### Post by ChipOManiac on 2011-02-17
I Solved The Problem. It Seems To Be That GTK-KDE4 Is The Application That Is Eating Up My Disk During StartUp.... As Well As Using Up A Lot Of My Memory

Killing The GTK-KDE4 Application Immediatley Gave The Results, The System Started Preforming The Way It Did.... After Giving This App A Full UnInstall, Didn't Experience Any Problems After That (I Hope) M:D

Many Thanks <<gordintoronto>> For Doing What You Could, Much Appreciated :D

---

