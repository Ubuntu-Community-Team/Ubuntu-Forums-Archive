---
title: "blank source list"
date: 2006-06-03
forum: General Help
---

### Post by serendipity576 on 2006-06-03
Hi everyone,
   Well I've had some trouble upgrading to Dapper and now everytime I sudo gedit etc/apt/sourcelist I can't see anything it all in the source list, it's completely blank.  What am I doing wrong?  I already used to synaptic to activate them all, but nothing.  

    Also if I were to do a fresh install, how could I do that without wiping out my Windows partition?  I can burn the iso, but then will it prompt me for what partition to install it on, and will this still be able to dual boot with Windows afterwards.  Sorry so many problems, I'm just getting frustrated and disheartened.  ](*,)

---

### Post by givré on 2006-06-03
Are you searching for /etc/apt/sourcelist or /etc/apt/sources.list i guess it is the second one ;)

---

### Post by serendipity576 on 2006-06-04
Well, I'm just wondering why the source list is blank when I open that window up.  I enabled and updated the repositories but it's still blank.  Any suggestions?:-k

---

### Post by xXx 0wn3d xXx on 2006-06-04
[QUOTE=serendipity576]Well, I'm just wondering why the source list is blank when I open that window up.  I enabled and updated the repositories but it's still blank.  Any suggestions?:-k[/QUOTE]
Just put the default sources.list back. Follow [ this guide to fix it. ](http://www.psychocats.net/ubuntu/sources.php)  Make sure you use the Dapper sources.list.

---

### Post by eqisow on 2006-06-04
If you are typing in "sudo gedit etc/apt/sourcelist" (just like that) then all you are doing is creating a new file. The correct command is "sudo gedit /etc/apt/sources.list".

Cheers :)

---

### Post by serendipity576 on 2006-06-05
ok I typed it in as "suod gedit etc/apt/sources.list".  That brought up the sources.list window and it was blank.  Well then I copy and pasted the Dapper sources and pasted them in there and when I hit save it said "Could not save, unexpected error--file not found"  I don't know what to do about that??:confused:

---

### Post by xXx 0wn3d xXx on 2006-06-05
[QUOTE=serendipity576]ok I typed it in as "suod gedit etc/apt/sources.list".  That brought up the sources.list window and it was blank.  Well then I copy and pasted the Dapper sources and pasted them in there and when I hit save it said "Could not save, unexpected error--file not found"  I don't know what to do about that??:confused:[/QUOTE]

That command should be:

> sudo gedit /etc/apt/sources.list

Try that and if that doesn't work, keep reading.

1. Open a terminal.

2. Type "gksudo nautilus" don't use quotes.

3. Go to /etc/apt/

3. Right click and go under "Create Document" and the click "Empty File."

4. Name it "sources.list" once again don't use quotes.

5. In terminal type: "sudo gedit /etc/apt/sources.list"

6. Replace the sources.list and click "Save."

That should work.

---

### Post by Sutekh on 2006-06-05
[quote=serendipity576]ok I typed it in as "suod gedit etc/apt/sources.list". That brought up the sources.list window and it was blank. Well then I copy and pasted the Dapper sources and pasted them in there and when I hit save it said "Could not save, unexpected error--file not found" I don't know what to do about that??:confused:[/quote] Again I think it is a simple typo.  If what you typed in the Terminal window is what you pasted here, you left out a '**/**' before etc

Copy this code and paste it in the Terminal window
```
sudo gedit **/**etc/apt/sources.list
``` Then paste the sources (if neeed)

---

### Post by serendipity576 on 2006-06-05
yep I'm stupid, it was a typo.  I typed the sudo gedit /etc/apt/sources.list and it opened the source.list window and the sources were already in there, so that worked out.  THanks for all the help guys. :p  In the future, how should I go about updating my repositories?

Clay

---

### Post by Sutekh on 2006-06-06
[quote=serendipity576]yep I'm stupid, it was a typo.  I typed the sudo gedit /etc/apt/sources.list and it opened the source.list window and the sources were already in there, so that worked out.  THanks for all the help guys. :p  In the future, how should I go about updating my repositories?

Clay[/quote]
I though that might be the case.  Not a problem if it worked out ok.

Well when someone talks about *updating* repositories I would take that to mean updating the package lists from the repositories, which you should do frequently so that you have the list of latest packages.  

Do this either by using
```
sudo apt-get update
```
or by clicking Reload in Synaptic.

Otherwise there is no need to 'update' repositories, they will look after themselves.  I'm specifically talking about official Ubuntu repositories, non-official ones often go down or move, so that may require 'updating' or changing the sources.list.

---

### Post by grizz_granlien on 2006-06-11
Thank you I tried this I deleted the source.list and rebuilt it and I am going to try it thanks for the info



[QUOTE=xXx 0wn3d xXx]Just put the default sources.list back. Follow [ this guide to fix it. ](http://www.psychocats.net/ubuntu/sources.php)  Make sure you use the Dapper sources.list.[/QUOTE]

---

