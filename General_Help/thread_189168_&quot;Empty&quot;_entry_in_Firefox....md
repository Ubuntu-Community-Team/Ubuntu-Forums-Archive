---
title: "&quot;Empty&quot; entry in Firefox..."
date: 2006-04-16
forum: General Help
---

### Post by aysiu on 2006-04-16
I filed [a bug report on it](https://launchpad.net/malone/bugs/39330) already, but apparently, it's not able to be reproduced by the developers (see screenshot of what my problem is).

Has anyone else experienced this? If so, any solutions you know of?

Here's my situation.

Used Breezy until last week. Already had 1.5.0.1 installed. Everything was working perfectly.

Upgraded to Dapper, the link to Mozilla's Firefox was replaced by Dapper's Firefox. Then this "empty" bookmarks entry behavior appeared. So, I thought, "Hm. Maybe it's Dapper's Firefox?" So I tired launching Mozilla's Firefox. Same behavior.

I tried it in KDE, Gnome, XFCE, using various themes. Same behavior.

I thought maybe my profile was corrupt, so I tried a different user. I tried the same user with a different (fresh) profile. Same behavior.

I even recently installed Firefox 1.5.0.2. Same behavior.

So is my computer a freak? Anyone else getting this?

I tried Googling around, and I couldn't find anything on this. And, of course, I've already filed a bug report. Not sure what else to do.

**Edit**: I said this in the bug report already, but for those of you who don't click on the link, the behavior is really strange--the first time I go into a folder in my bookmarks, the "empty" entry appears. If I go back into that folder in the same session of Firefox, it's gone. However, if I close Firefox and open up a new session, the "empty" entry reappears.

---

### Post by m.musashi on 2006-04-16
That is odd. I have the same exact folder just without the "empty" entry. I suppose it's like the noise your car makes but never when there is a mechanic around :).

Have you tried to go into the manage bookmarks and view the contents there? I'm not sure what that would tell us though. Can you delete this "empty" entry? Just wondering if it's a ghost entry (i.e. you can see it but the computer doesn't know it's there - I had that with icons before).

I have noticed few odd things in flight 6. I still can't figure out why my icons in Oo.o disappear.

Oh, one more thing. In the bug report you mentioned that the "empty" entry is circled in red and real ones in green. I don't see that. Can you explain what you mean? Or are you referring to how the entry you point to "lights up"? Mine do that is blueish gray. Must be related to the theme. Are you using a firefox theme?

---

### Post by aysiu on 2006-04-16
Thanks for responding. [QUOTE=m.musashi]
Have you tried to go into the manage bookmarks and view the contents there? I'm not sure what that would tell us though. Can you delete this "empty" entry? Just wondering if it's a ghost entry (i.e. you can see it but the computer doesn't know it's there - I had that with icons before).[/quote] Yeah, I can't see it in Manage Bookmarks.

> 
Oh, one more thing. In the bug report you mentioned that the "empty" entry is circled in red and real ones in green. I don't see that. Can you explain what you mean? Or are you referring to how the entry you point to "lights up"? Mine do that is blueish gray. Must be related to the theme. Are you using a firefox theme? Sorry. I had a different screenshot I was trying to attach in an email. I realized afterwards that I was just posting to the bug report and not really sending an email. Those "red" and "green" circles don't exist in the current screenshot.

---

### Post by m.musashi on 2006-04-16
No problem. Not sure how much help I can be, though.

Since you can't see it in manage bookmarks that suggests that FF doesn't "know" it's there. I don't know much about the inner workings of FF but themes can cause odd behavior. Are you running the default theme or something added.

You mentioned this is an upgrade from Breezy and that "the link to Mozilla's Firefox was replaced by Dapper's Firefox." Both my Breezy and Dapper computers have the same link. What is different about Dapper (other than it uses 1.5.0.1)? You have version 1.5.0.2? Is that a recent update? I just updated yesterday and I'm still running 1.5.0.1. Is yours from the repositories or a manual install?

I did try the upgrade from Breezy to Dapper but it didn't work well so I did a clean install. Perhaps it's related to upgrading. I've heard some people have this work fine but I think I've heard more say there were a lot of problems.

As for your computer being a freak, that may be the case :). Or something odd with Dapper. I've been using it for a couple months and although it's been working fine, I do have a handful of odd issues that I hope will get resolved by the final release.

---

### Post by aamukahvi on 2006-04-16
I had a manual install of Firefox 1.5 on Breezy, but I removed it before dist-upgrading to Dapper. Figured it might do bad things(tm). :p

---

### Post by towsonu2003 on 2006-04-16
I am pretty sure this will not give insight at all, but is the entry visible with a text editor? 
nano ~/.mozilla/firefox/<randomnumbers>.default/bookmarks.html

<randomnumbers> as name of your profile folder

edit: the place of profile may be different in dapper, above post was with breezy.

---

### Post by aysiu on 2006-04-16
[QUOTE=towsonu2003]I am pretty sure this will not give insight at all, but is the entry visible with a text editor? 
nano ~/.mozilla/firefox/<randomnumbers>.default/bookmarks.html

<randomnumbers> as name of your profile folder

edit: the place of profile may be different in dapper, above post was with breezy.[/QUOTE] Yes, it's visible. Here's the first part: ```
<!DOCTYPE NETSCAPE-Bookmark-file-1>
<!-- This is an automatically generated file.
     It will be read and overwritten.
     DO NOT EDIT! -->
<META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=UTF-8">
<TITLE>Bookmarks</TITLE>
<H1 LAST_MODIFIED="1144898781">Bookmarks</H1>

<DL><p>
    <DT><H3 ADD_DATE="1137225339" LAST_MODIFIED="1144898781" PERSONAL_TOOLBAR_FOLDER="true" ID="rdf:#$YpC2E3">Bookmarks Toolbar Folder</H3>
    <DL><p>
    </DL><p>
    <DT><H3 ADD_DATE="1127878658" LAST_MODIFIED="1141524396" ID="rdf:#$RrTOe2">Linux</H3>
    <DL><p>
        <DT><A HREF="http://www.ubuntuforums.org/search.php?do=getnew" ADD_DATE="1127076264" LAST_VISIT="1145075031" LAST_MODIFIED="1127782857" ICON="data:$
        <DT><A HREF="http://www.linuxquestions.org/questions/forumdisplay.php?forumid=63" ADD_DATE="1130990649" LAST_VISIT="1145228144" ICON="data:image/x-$
        <DT><A HREF="http://www.kubuntuforums.net/forums/index.php?action=unread" ADD_DATE="1134860059" LAST_VISIT="1145228144" LAST_MODIFIED="1134860084" $
    </DL><p>
``` I don't believe it has anything to do with my bookmarks, though, because if I use a fresh profile (no .mozilla folder, and Ubuntu just generates a new one), I still have the same problem.

---

### Post by towsonu2003 on 2006-04-16
you might wanna post that to the bug report. has add date and last modify date. may be they can make sense of it? 

also, check out the contents of the 
/opt/firefox/defaults/profile/bookmarks.html (equivalent of this in dapper???) (with the text editor) which, I guess, is the bookmarks.html created by default when there is no profile in place. copy pasting that to the bug report as well might be a good idea, bc it will have the original add & modify dates (from the time dapper updated that file???)... 

PS. sorry I couldn't check the bug report. takes long to open that site with dial up.

---

### Post by m.musashi on 2006-04-17
Wow, I can't make head or tails of that file. However, I'm wondering how or what firefox uses to set up a new profile. In other words, how do the initial bookmarks get added to a new install or when you add a new user? There must be some default option or script that runs. I don't know what or where that might be but if there is a way to find and view it you might be able to see if something is adding the "empty" entry.

Just a though.

EDIT: One more thing. Aysiu, I'm looking through the section of the bookmarks.html file that you posted and I cannot see any entry for the "empty" entry. What I do see is a folder called "Bookmarks Toolbar Folder" that appears to be empty and a folder called "Linux" that has entries for
[www.ubuntuforums.org](www.ubuntuforums.org)
[www.linuxquestions.org](www.linuxquestions.org)
[www.kubuntuforums.net](www.kubuntuforums.net)

What I can't see is the folder for "Ubuntu and Free Software links" that contained the "empty" entry as in your screen shot in the first post. Did you snip before that section or does it not show up? Or am I just not seeing it?

---

### Post by elsupermang on 2006-04-17
I believe the default bookmarks is loaded from /usr/lib/firefox/defaults/profile/bookmarks.html

---

### Post by towsonu2003 on 2006-04-17
I'll speak in breezy terms with firefox installed using the wiki. adjust your paths ;)

I'm pretty sure firefox just copies over the /opt/firefox/defaults/profile/ as ~/.mozilla/firefox/<randomnumbers>.default. The /opt/firefox/defaults/profile/ is extracted when you untar the initial installation tar.gz file. So basically, assuming that the "empty" is inside /opt/firefox/defaults/profile/bookmarks.html file as well:

1. Datestamps in /opt/firefox/defaults/profile/bookmarks.html will show when that file was changed, possibly via an apt-get (dist-)upgrade (this is for dapper), hence pointing to what upgrade broke things. 

2. if /opt/firefox/defaults/profile/bookmarks.html is fixed in the repos, an apt-get upgrade will fix azz' bug after new profile. You probably just need to delete the bugged lines in ~/.mozilla/firefox/<randomnumbers>.default/bookmarks.html to fix it without a new profile.

edit:
[quote=elsupermang]I believe the default bookmarks is loaded from **/usr/lib/firefox/defaults/profile/**bookmarks.html[/quote]

---

### Post by aysiu on 2006-04-17
[QUOTE=m.musashi]Wow, I can't make head or tails of that file. However, I'm wondering how or what firefox uses to set up a new profile. In other words, how do the initial bookmarks get added to a new install or when you add a new user? There must be some default option or script that runs. I don't know what or where that might be but if there is a way to find and view it you might be able to see if something is adding the "empty" entry.[/QUOTE] Yeah, but what's weirding me out is the fact that the empty entry disappears after you've looked at that folder once.

Launch up Firefox. Look at a folder the first time--the "empty" entry is there. Same session: look at the folder a second time--it's gone.

I don't know if it's worth pursuing this bug report, because the problem doesn't seem to be widespread (I searched all over the internet and found only one other instance of this bug... it was actually on Mozilla's bugzilla, and from last year--the bug was closed because no one else reported having this problem), and it's not reproduceable.

I think I'm just going to live with it. When Dapper gets released in June, I'll do a clean reinstall and see if the bug persists.

Thanks to all who tried to help.

**Edit**: townsonu2003, I'll try that fix--let you know how it goes.

---

### Post by m.musashi on 2006-04-17
[QUOTE=aysiu]Yeah, but what's weirding me out is the fact that the empty entry disappears after you've looked at that folder once.[/quote]
I noticed that that bookmarks.html file gets rewritten all the time. It's possible it's there and then rewritten and removed...for some reason.

> I don't know if it's worth pursuing this bug report, because the problem doesn't seem to be widespread (I searched all over the internet and found only one other instance of this bug... it was actually on Mozilla's bugzilla, and from last year--the bug was closed because no one else reported having this problem), and it's not reproduceable.
Maybe not, but it's fun to try. It's these types of problems that have helped me move from total noob to semi-knowledgeable.

---

### Post by towsonu2003 on 2006-04-17
[QUOTE=aysiu]
I don't know if it's worth pursuing this bug report, because the problem doesn't seem to be widespread (I searched all over the internet and found only one other instance of this bug... it was actually on Mozilla's bugzilla, and from last year--the bug was closed because no one else reported having this problem), and it's not reproduceable.[/QUOTE]
reopen it ;) I find reopening wontfix or worksforme bugs very entertaining.

---

### Post by towsonu2003 on 2006-04-17
[QUOTE=m.musashi]I noticed that that bookmarks.html file gets rewritten all the time. It's possible it's there and then rewritten and removed...for some reason.
[/QUOTE]
is it possible firefox understands something is wrong with the file and fixes it? 

PS. sorry for kinda double posting...

---

### Post by m.musashi on 2006-04-17
[QUOTE=towsonu2003]You probably just need to delete the bugged lines in ~/.mozilla/firefox/<randomnumbers>.default/bookmarks.html to fix it without a new profile.[/QUOTE]
I'm not sure that will work. This file seems to get rewritten every time you open FF. I had it open to try changing it (it says not too but you know...) and while it was open I opened FF. When I went to save it I was told the file had changed and did I really want to save it.

---

### Post by m.musashi on 2006-04-17
[QUOTE=towsonu2003]is it possible firefox understands something is wrong with the file and fixes it? 

PS. sorry for kinda double posting...[/QUOTE]
Maybe, that would be cool. However, it comes back the next time so it's not a permanent fix.

---

### Post by towsonu2003 on 2006-04-17
[QUOTE=m.musashi]I'm not sure that will work. This file seems to get rewritten every time you open FF. I had it open to try changing it (it says not too but you know...) and while it was open I opened FF. When I went to save it I was told the file had changed and did I really want to save it.[/QUOTE]
what happens when you open the file, change it, save and close, and open firefox? 

I'd do 
1. open, modify, save, close ~/.mozilla/firefox/<randomnumbers>.default/bookmarks.html

2. copy ~/.mozilla/firefox/<randomnumbers>.default/bookmarks.html to ~/.mozilla/firefox/<randomnumbers>.default/bookmarks.html2

**edit: forgot step** 3. open firefox, browse a bit, close firefox

4. diff ~/.mozilla/firefox/<randomnumbers>.default/bookmarks.html ~/.mozilla/firefox/<randomnumbers>.default/bookmarks.html2 to see what's changed.

---

### Post by aysiu on 2006-04-17
Unfortunately, I'm at work (on a Windows machine), so I'll have to try all this when I get home. I'll let you know then.

---

### Post by m.musashi on 2006-04-17
[QUOTE=towsonu2003]what happens when you open the file, change it, save and close, and open firefox? 

I'd do 
1. open, modify, save, close ~/.mozilla/firefox/<randomnumbers>.default/bookmarks.html

2. copy ~/.mozilla/firefox/<randomnumbers>.default/bookmarks.html to ~/.mozilla/firefox/<randomnumbers>.default/bookmarks.html2

3. diff ~/.mozilla/firefox/<randomnumbers>.default/bookmarks.html ~/.mozilla/firefox/<randomnumbers>.default/bookmarks.html2 to see what's changed.[/QUOTE]
Gave this a try. I added an entry for Google in the "Ubuntu and free software links" folder under bookmarks. When I compare, a couple BBC news links changed and my addition of Google was gone. I then tried to take something away. When I take out a link to ubuntu it stayed out. Perhaps it didn't like what I added and just removed it or there is something that prevents adding. However, it does let you take away stuff. At least in my quick test.

EDIT: Played with this a bit more and I have been able to manually add a google entry in bookmarks.html. I think I did something wrong the first time - maybe bad syntax. Entries that I deleted did not "magically" return, but I was able to add them back in manually. Interestingly enough, they only "came back" after I actually connected to the network. I had been playing offline.

Not sure if any of this helps with aysiu's original problem. It seems as if the "empty" entry regenerates itself. I cannot reproduce this with any of the other links, however. Those that are deleted are gone for good and those that are added stay. What does seem to change are the RSS feeds but I don't think that is related. If you can find the "empty" entry in the bookmarks.html file and delete it, try and see what happens.

---

### Post by aysiu on 2006-04-17
[QUOTE=towsonu2003]what happens when you open the file, change it, save and close, and open firefox? 

I'd do 
1. open, modify, save, close ~/.mozilla/firefox/<randomnumbers>.default/bookmarks.html

2. copy ~/.mozilla/firefox/<randomnumbers>.default/bookmarks.html to ~/.mozilla/firefox/<randomnumbers>.default/bookmarks.html2

**edit: forgot step** 3. open firefox, browse a bit, close firefox

4. diff ~/.mozilla/firefox/<randomnumbers>.default/bookmarks.html ~/.mozilla/firefox/<randomnumbers>.default/bookmarks.html2 to see what's changed.[/QUOTE] Okay, I tried this out and just got a lot of gibberish. Here's an excerpt: ```
+/P/8//7//P/+///9/////////////////////////f7+//7/+//+/P//29v3/wsMzv8BAtj/AgHa/wAA2/8JCc7/z9X0//3//P/+/v//+v3+/+rx/P9Ceuj/CUnx/wZI9v8bXez/wdP2/77j+P8Kk/n/ApL8/wyW+P/R7vv//v3///z//v/+//7//P7///3//////////////////////f///f7+///9/v/6/P3/XlzX/wEB2/8BAtb/AgDc/wED1P+cnuP//v7+//7+/v///vv/j6vy/wVK+f8DSPr/BEn8/wNI/P84bev/8Pr//yqj8/8Fkf7/NqLx//D8/f/9//7//v/9///+//////3////+//////////////////7//v/9//////7///z//v+pqOn/KCjU/yco0v8uKNb/KCbU/4mJ3v///v7/+//+//v+/v9fje//Akr9/wFL/P8ASf7/A0n9/xBS6P/z+/3/SK7y/wKS/v9Grvb/9v3////////////////////////////////////////////////+/////v/8/////P7///z9/v/4+/7/9/v///r8/f/6+v7/+f39//7+/f/+/v7//v3+/4ir9P8GSvn/BEj5/wRI/f8ESfr/NWvr//L7/f8vo/T/AZL//0Kr9P/1/v3//v////////////////////////////////////////////3//P////z//v/+//3/6PD6/8rZ8v/H2PP/yNn0/8fZ8//f6fb/+v78///+/v/7/v7/6/H8/0l67P8JSe7/BUn0/x1g7f/C0fj/uOP6/weT+v8Bkv3/JZn1/+n4/P/+/////////////////////////////////////////////v/8///////7//z9/P+CqfL/B03w/whM9f8IS/f/CEv1/4qk7v/9/vz//f/9/////P/7//3/9Pj+/8nW9/++y/P/5O77/83o+v8rn/j/A5H//wGV+v8Ikvv/sd34//3+/v/+/v///v/+//z////////////////////+/////v////3+///8/v3/8Pn//zdw6/8BSf7/Akf//wFK/v8ESvj/rMby//7+/f/+//3///////////////////////7//v/8//7/f8Xy/wOV+/8Ck/3/AZL//wSR/v9BqvP/6/r9//z+/v/+/vz//f7+//z//f/9//3//v7//////f/+//3///7+//v9/P+jvvX/Bkr1/wBK/v8BSf3/BEf+/xZY8P/g7v3//P/8//39/v/////////////////+//7//f3+//v+/P/P6Pr/DJP3/wSS/v8Ckv//BJL+/wWS/P9svPn/8vv8//r+/v/9/vz//v3+//7+///+//3//f3+//n+/v/9/vz/0d36/x1b7v8FSfz/Akj//wFK/v8DSvr/YIzx//z9/v/8/v3///3+//////////////////7////+/v///P/+//b++/9Yufb/BJH+/wGT/v8BlPz/A5P8/xmY+P/Z7fv/+v77//z8+//8/vr/+f7+///+/f/8/vr/9/n8/6jB9/8dX+v/AEr6/wFI//8BSP7/BUr4/xFS8f/N2vj///7///3+//////7//////////////////v////3//v/9//7///3//9vt+/8Wl/X/BZL9/wKQ/v8Ck/r/dMX4//n8/v+zx/D/bZnt/7jI8//J1/v/v9L3/5Sw8/9Kee7/CEz0/wxM8/8vZ/T/NW/w/w5Q8P8FSPf/c6Dt//v9/v/8//3//v/+//3//f///////////////////////////////////////v///6/b+P8Vlff/AZP9/yuc8v/j8/3/8PP9/zds7P8BSP3/A0v5/wlJ9v8DSfr/Akj+/wJL9v9Jeuv/zt77//X4///y+f//5O3+/6K67//t9/3///7+////////////////////////////////////////////////////////////+v38/6DY+P8alvP/nNT2//v+/v+Mr/T/Bkj0/wRK+P8BSf3/AEn9/wNI/f8BSfz/O3Hu/+zx/f+Um+X/MjHS/ycmzf9zct3/7O/4//z+/P/6//3////////////////////////////////////////////////////////////+/v//+v7+/8jr/P/u+f7/1+n8/x9Z8P8FSfv/AUj+/wVG//8BSv3/BEj8/wZM9P+vxPP/tLPs/wgH1P8EAdj/AQHa/wED1P9oatj//vv+//7+/v////////////////////////////////////////////////////////////7+//////v/+f79//7+/P+/0vH/L2Xt/wtM9P8FSfz/Akn+/wBJ//8CSf3/FE/y/9vl+f9gX9//AQLT/wMA2v8AAtf/BQDW/x8fzv/w7/3//v39//////////////////////////////////////////////////////////////////////////////////z+/f/y8/7/yNX4/46t8v9ok+7/X4rr/2aM6/+DoO7/7fH8/2ln4P8CAtX/AQDe/wEC1f8BA9T/JiTK/+/0/v///v7//////////////////////////////////////////////////////////////////////////////////f3+//7++f/+/vz/+/7+//v+/v/8/f7/+vz+//n+/P/+/fr/x8bu/xEPyv8BANv/AgHb/wYD1P+FgeD//v38//z//v/////////////////////////////////////////////////////////////////////////////////9/v///f7///z//v/+//7//f7//////f////3////4//z8/v/9/P3/xsDw/1lb1P9ST9T/nZ/i//j5/f/+//7///3///////////////////////////////////////////////////////////////////////////////////7//f////7///7+//3+/P/9/v7//v79//v9///+/vz/+//9//79///8/v3/+/39//n7/f/9/vz//v3+//79/v/9//z/////////////////AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA=" LAST_CHARSET="UTF-8" ID="rdf:#$zYGhD3">Ubuntu packages</A>
<         <DT><A HREF="http://www.ubuntuforums.org/showthread.php?t=22646" ADD_DATE="1125761665" LAST_VISIT="1145232016" ICON="data:image/x-icon;base64,AAABAAEAICAAAAAAAACoEAAAFgAAACgAAAAgAAAAQAAAAAEAIAAAAAAAABAAAA
``` It goes on and on like that for pages.

I appreciate everyone's help, but I don't think this one is going to be solved, especially since it occurs for both Ubuntu's Firefox *and* Mozilla's Firefox. Incidentally, I did try ```
sudo apt-get install --reinstall firefox
``` and downloading a fresh .tar.gz from Mozilla--neither worked.

My test Ubuntu computer works just fine, though (on this one, I did a fresh Breezy server install, dist-upgraded to Dapper, and then installed Xubuntu on top of it). It's just my main computer that has this problem, so maybe I'll wait until Dapper comes out officially and just reinstall the whole OS.

Again, I appreciate everyone's willingness to help me out.

---

### Post by aysiu on 2006-04-18
Reinstalled last night. Works perfectly now.

---

### Post by m.musashi on 2006-04-18
[QUOTE=aysiu]Okay, I tried this out and just got a lot of gibberish. Here's an excerpt: ```
+/P/8//7//P/+///9/////////////////////////f7+//7/+//+/P//29v3/wsMzv8BAtj/AgHa/wAA2/8JCc7/z9X0//3//P/+/v//+v3+/+rx/P9Ceuj/CUnx/wZI9v8bXez/wdP2/77j+P8Kk/n/ApL8/wyW+P/R7vv//v3///z//v/+//7//P7///3//////////////////////f///f7+///9/v/6/P3/XlzX/wEB2/8BAtb/AgDc/wED1P+cnuP//v7+//7+/v///vv/j6vy/wVK+f8DSPr/BEn8/wNI/P84bev/8Pr//yqj8/8Fkf7/NqLx//D8/f/9//7//v/9///+//////3////+//////////////////7//v/9//////7///z//v+pqOn/KCjU/yco0v8uKNb/KCbU/4mJ3v///v7/+//+//v+/v9fje//Akr9/wFL/P8ASf7/A0n9/xBS6P/z+/3/SK7y/wKS/v9Grvb/9v3////////////////////////////////////////////////+/////v/8/////P7///z9/v/4+/7/9/v///r8/f/6+v7/+f39//7+/f/+/v7//v3+/4ir9P8GSvn/BEj5/wRI/f8ESfr/NWvr//L7/f8vo/T/AZL//0Kr9P/1/v3//v////////////////////////////////////////////3//P////z//v/+//3/6PD6/8rZ8v/H2PP/yNn0/8fZ8//f6fb/+v78///+/v/7/v7/6/H8/0l67P8JSe7/BUn0/x1g7f/C0fj/uOP6/weT+v8Bkv3/JZn1/+n4/P/+/////////////////////////////////////////////v/8///////7//z9/P+CqfL/B03w/whM9f8IS/f/CEv1/4qk7v/9/vz//f/9/////P/7//3/9Pj+/8nW9/++y/P/5O77/83o+v8rn/j/A5H//wGV+v8Ikvv/sd34//3+/v/+/v///v/+//z////////////////////+/////v////3+///8/v3/8Pn//zdw6/8BSf7/Akf//wFK/v8ESvj/rMby//7+/f/+//3///////////////////////7//v/8//7/f8Xy/wOV+/8Ck/3/AZL//wSR/v9BqvP/6/r9//z+/v/+/vz//f7+//z//f/9//3//v7//////f/+//3///7+//v9/P+jvvX/Bkr1/wBK/v8BSf3/BEf+/xZY8P/g7v3//P/8//39/v/////////////////+//7//f3+//v+/P/P6Pr/DJP3/wSS/v8Ckv//BJL+/wWS/P9svPn/8vv8//r+/v/9/vz//v3+//7+///+//3//f3+//n+/v/9/vz/0d36/x1b7v8FSfz/Akj//wFK/v8DSvr/YIzx//z9/v/8/v3///3+//////////////////7////+/v///P/+//b++/9Yufb/BJH+/wGT/v8BlPz/A5P8/xmY+P/Z7fv/+v77//z8+//8/vr/+f7+///+/f/8/vr/9/n8/6jB9/8dX+v/AEr6/wFI//8BSP7/BUr4/xFS8f/N2vj///7///3+//////7//////////////////v////3//v/9//7///3//9vt+/8Wl/X/BZL9/wKQ/v8Ck/r/dMX4//n8/v+zx/D/bZnt/7jI8//J1/v/v9L3/5Sw8/9Kee7/CEz0/wxM8/8vZ/T/NW/w/w5Q8P8FSPf/c6Dt//v9/v/8//3//v/+//3//f///////////////////////////////////////v///6/b+P8Vlff/AZP9/yuc8v/j8/3/8PP9/zds7P8BSP3/A0v5/wlJ9v8DSfr/Akj+/wJL9v9Jeuv/zt77//X4///y+f//5O3+/6K67//t9/3///7+////////////////////////////////////////////////////////////+v38/6DY+P8alvP/nNT2//v+/v+Mr/T/Bkj0/wRK+P8BSf3/AEn9/wNI/f8BSfz/O3Hu/+zx/f+Um+X/MjHS/ycmzf9zct3/7O/4//z+/P/6//3////////////////////////////////////////////////////////////+/v//+v7+/8jr/P/u+f7/1+n8/x9Z8P8FSfv/AUj+/wVG//8BSv3/BEj8/wZM9P+vxPP/tLPs/wgH1P8EAdj/AQHa/wED1P9oatj//vv+//7+/v////////////////////////////////////////////////////////////7+//////v/+f79//7+/P+/0vH/L2Xt/wtM9P8FSfz/Akn+/wBJ//8CSf3/FE/y/9vl+f9gX9//AQLT/wMA2v8AAtf/BQDW/x8fzv/w7/3//v39//////////////////////////////////////////////////////////////////////////////////z+/f/y8/7/yNX4/46t8v9ok+7/X4rr/2aM6/+DoO7/7fH8/2ln4P8CAtX/AQDe/wEC1f8BA9T/JiTK/+/0/v///v7//////////////////////////////////////////////////////////////////////////////////f3+//7++f/+/vz/+/7+//v+/v/8/f7/+vz+//n+/P/+/fr/x8bu/xEPyv8BANv/AgHb/wYD1P+FgeD//v38//z//v/////////////////////////////////////////////////////////////////////////////////9/v///f7///z//v/+//7//f7//////f////3////4//z8/v/9/P3/xsDw/1lb1P9ST9T/nZ/i//j5/f/+//7///3///////////////////////////////////////////////////////////////////////////////////7//f////7///7+//3+/P/9/v7//v79//v9///+/vz/+//9//79///8/v3/+/39//n7/f/9/vz//v3+//79/v/9//z/////////////////AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA=" LAST_CHARSET="UTF-8" ID="rdf:#$zYGhD3">Ubuntu packages</A>
<         <DT><A HREF="http://www.ubuntuforums.org/showthread.php?t=22646" ADD_DATE="1125761665" LAST_VISIT="1145232016" ICON="data:image/x-icon;base64,AAABAAEAICAAAAAAAACoEAAAFgAAACgAAAAgAAAAQAAAAAEAIAAAAAAAABAAAA
``` It goes on and on like that for pages.[/QUOTE]
Glad to hear it's working. FYI, all this gibberish seems to be what tells firefox how to draw the icons that appear in the bookmarks menu. I haven't figured out how it works yet. My first thought was that it gave color in hex for each pixel but that doesn't seem right. In any case, until you raised this issue I never even thought about it. So thanks for the opportunity to learn something new.

---

### Post by aysiu on 2006-04-20
Okay.

I was able to reproduce the problem.

Any guinea pigs out there want to see if it's totally reproduceable or just my freaky computer?

So the original problem came about when I upgraded to Dapper. At the time (before I upgraded to Dapper), I had Kubuntu, Ubuntu, and Xubuntu installed.

Then, recently, I did a reinstall of Dapper (just Kubuntu). The problem went away.

Today, I added Ubuntu and Xubuntu to it, and the problem came back! Good thing I added them using *aptitude* instead of *apt-get*. So I removed Xubuntu. Problem was still there. Then, I removed Ubuntu. The problem went away.

So it appears to be when you combine Ubuntu and Kubuntu on Dapper that the "empty" entry appears. Can anyone confirms that this happens not just on my computer?

I've already updated the bug report.

---

### Post by m.musashi on 2006-04-20
[QUOTE=aysiu]Okay.

I was able to reproduce the problem.

Any guinea pigs out there want to see if it's totally reproduceable or just my freaky computer?[/quote]
Ah, a challenge...

> Today, I added Ubuntu and Xubuntu to it, and the problem came back! Good thing I added them using *aptitude* instead of *apt-get*. So I removed Xubuntu. Problem was still there. Then, I removed Ubuntu. The problem went away.

So it appears to be when you combine Ubuntu and Kubuntu on Dapper that the "empty" entry appears. Can anyone confirms that this happens not just on my computer?
I installed ubuntu dapper and then added (via apt-get as I haven't been able to break that habbit:)) kubuntu-desktop and xubuntu-desktop. It was a while back but I never noticed this issue. I wonder if it's a kubuntu with added ubuntu that is the issue or if it happens both ways, so to speak.

Did you install flight 6?. I have flight 5 (upgraded) but that could be a clue. I've been wanting to clean everything up and start again so this could be a good reason. Maybe I'll start this time with aptitude too.

---

### Post by aysiu on 2006-04-20
> **m.musashi]
I installed ubuntu dapper and then added (via apt-get as I haven't been able to break that habbit:)) kubuntu-desktop and xubuntu-desktop. It was a while back but I never noticed this issue. I wonder if it's a kubuntu with added ubuntu that is the issue or if it happens both ways, so to speak.[/quote] That could be it--something in Ubuntu added to Kubuntu breaking Firefox somehow said:**
> 
Did you install flight 6?. I have flight 5 (upgraded) but that could be a clue. I've been wanting to clean everything up and start again so this could be a good reason. Maybe I'll start this time with aptitude too. I don't have flight anything. I did a server Breezy install, dist-upgraded to Dapper, and then installed Kubuntu on top of that. I've been dist-upgrading every day, so I have whatever's the latest.

---

### Post by towsonu2003 on 2006-04-20
[QUOTE=aysiu]Or, it could just be my freaky computer.
[/QUOTE]
you reproduced the bug, which means your computer is doing fine (especially if it can handle all that upgrading and distgrading ;) )

unfortunately, I can't reproduce your bug: I have no broadband and no spare computer... sorry

---

### Post by aysiu on 2006-04-20
[QUOTE=towsonu2003]you reproduced the bug, which means your computer is doing fine (especially if it can handle all that upgrading and distgrading ;) )[/quote] Okay. Well, if a brave soul with broadband could try installing Kubuntu Dapper and then putting Ubuntu on top of it to see if the Firefox folders have weird empty entries, that'd be great... and tack it on to the bug report!

---

### Post by m.musashi on 2006-04-20
[QUOTE=aysiu]Okay. Well, if a brave soul with broadband could try installing Kubuntu Dapper and then putting Ubuntu on top of it to see if the Firefox folders have weird empty entries, that'd be great... and tack it on to the bug report![/QUOTE]
For some reason I enjoy doing installs so I'll give this a try when I get home tonight.

One thought, however, is that the bug manifests itself through the dist-upgrade from breezy rather than something inherent in the dapper install. In other words, there may be some remnant from breezy. I don't really know the inner workings of the upgrade process but I'm betting it just overwrites flies and perhaps something in firefox isn't getting overwritten. I do know that the default bookmarks in dapper are different from those in breezy. If it is just appending the bookmark file rather than overwriting it that could be what is causing the problem. My guess is that it wouldn't overwrite because that would cause you to lose all your bookmarks. At least that is my working theory. Feel free to poke holes in it.

EDIT: of course if you are doing a server install that might not install firefox at all. I don't know what all gets installed this way.

---

### Post by aysiu on 2006-04-20
[QUOTE=m.musashi]
EDIT: of course if you are doing a server install that might not install firefox at all. I don't know what all gets installed this way.[/QUOTE] A server install definitely does not install Firefox. There may be something to your upgrade v. clean install theory, though.

It's still a bug, though, as many people will just dist-upgrade Breezy instead of doing a clean reinstall.

---

### Post by m.musashi on 2006-04-24
Okay, finally had a chance to try this. Unfortunately, I wasn't able to dist-upgrade from breezy at all. I kept getting errors about not finding some of the repositories. I did this from work and our network seems to have problems from time to time. I'll see if I have better luck at home.

---

### Post by aysiu on 2006-06-04
So, I already posted about this [here](http://www.ubuntuforums.org/showthread.php?t=161154), but the thread got closed, since it was in the Dapper development section of the forum.

I was wondering if anyone had any new insights.

Basically, starting with Dapper--this wasn't a Breezy or Hoary problem (and you can read the original thread for more details):

If I install Gnome, my Firefox gets screwed up so that an "empty" entry appears in each subfolder of my bookmarks. It appears only the first time I view that folder in one session. The next time I view the folder during that session, it's gone again.

At first, I thought it was some combination of adding Gnome to KDE, but when I had both KDE and Gnome on my *other* computer, the problem didn't exist, and I've searched around, and apparently no one else is experiencing this problem.

When I did a clean install of KDE, the problem went away.

When I did a clean install of Gnome, it came back.

If I use a fresh profile (delete the .mozilla folder), the problem still persists. If I create a new user, the problem still persists.

The problem occurs with both the Ubuntu Firefox *and* the Mozilla Firefox.

Now, here's where it gets weirder--if I launch Firefox as root (*gksudo firefox*), the problem doesn't exist.

So does anyone know how I can replicate the settings so that my regular user can do... whatever root does to get rid of the "empty" entries altogether?

I could just have KDE and ditch Gnome, but I kind of like both. I can also just live with the "empty" entry, but it seems silly.

I'm just a little baffled about this, since I appear to be the only one experiencing this, and it happens on only one of my computers, not the other.

Any theories or experiments to try out would be much appreciated.

Filing a bug report did not help, since the developers could not reproduce the error.

---

### Post by syntax on 2006-06-04
Do you have "Enable assistive technologies" checked by any chance?  I've noticed that same behavior when this is checked.

---

### Post by aysiu on 2006-06-04
[QUOTE=syntax]Do you have "Enable assistive technologies" checked by any chance?  I've noticed that same behavior when this is checked.[/QUOTE] Oh, my God! I can't believe that's it. **Thank you**.

Now, does that qualify as a bug report, since it's reproduceable?

---

