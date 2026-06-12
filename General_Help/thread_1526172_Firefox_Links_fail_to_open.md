---
title: "Firefox Links fail to open"
date: 2010-07-07
forum: General Help
---

### Post by sandman3838 on 2010-07-07
Hello

Lately I have been rather disappointed with Firefox on Ubuntu 10.04.  It was running rather slow, some sites where taking up to 40 to 50 sec to load, while on my other systems using other OS I had no issues.  So I checked around and Opera and Swiftfox looked very good.  Wow what a difference both were great!  However being an old Firefox user I'm leaning towards Swiftfox.

Now here is my problem.  

At time there are web sites that I wish to go back to but I really don't wish to save them in bookmarks.  So I just drag the Address Line (SCREENSHOT_1) to a folder or desktop (SCREENSHOT_2).  At the moment SWIFTFOX is my default Web Browser and I have removed Firefox.  None of these older Web Links will open to Swiftfox, it tries to open but nothing happens.  Even if I try and drag a new one from Swiftfox, and later go back to that Web Link will not open.  The properties on one of these files can be seen with (SCREENSHOT_3).

Suggestions anyone??

Thank you for your help.

---

### Post by lovinglinux on 2010-07-09
Your original Firefox problem looks more like a network issue.

Have you tried to disable ipv6 to see if Firefox loads pages faster? Have you tried to create a new profile to see if the problem goes away?

Swiftfox is basically Firefox complied with optimizations for each processor family. It usually runs faster because of that. But it is closed source.

Can you attach one of those links to test here?

---

### Post by sandman3838 on 2010-07-09
Hello and thanks for the help.

I just tried to do as you suggested and make/drag a new Web Link to Google to my desktop:

[http://www.google.com/webhp?sourceid=navclient-ff](http://www.google.com/webhp?sourceid=navclient-ff)


However what I got was something new.   
 ](*,) See new screen-shot.

I do have another Web Link saved off in another folder, it too fails to open.  See file attachment!
(I had to compress it to make it a valid)

As for your suggestion about IPV6?  Do you really think so.....
I have access to Email and the Internet through Swiftfox and Thunderbird and my bookmarks within Swiftfox work just fine.

Since writing my original posting I found this (below), what do you think, could it be a possible issue that the system just doesn't know what to do with the file?   After looking over this new information, please let me know which route to take.  Your input is really appreciated.

****** Notes other case? ****** 

In the /usr/share/applications/defaults.list , text/html (among others) was pointing to firefox-2.desktop. A simple change of the entry to firefox.desktop for the current version of Firefox took care of the problem. Desktop URLs now open in the browser. 

********************************** 

==== Now these are the three lines that mention HTML in my Defaults list file ===

text/html=firefox.desktop;google-chrome.desktop

application/xhtml_xml=google-chrome.desktop

application/xhtml+xml=firefox.desktop

---

### Post by sandman3838 on 2010-07-09
I don't know if it would help but here are another two web links that I was unable to copy to the desktop.  One is for Amazon.com and the other is for 1MDB.

You know before I was able to drag the link to the desktop but now it won't.  

The only thing that I have done different was a total removal and reinstall of Thunderbird, Firefox and Swiftfox.

---

### Post by lovinglinux on 2010-07-10
I have tested here and Swiftfox can't open the link by dragging, but can by double clicking. I think this has something to do with the ubufox (Ubuntu Firefox Modifications) extension. Swiftfox simply opens it as a text file instead of opening the contained link. Additionally, I'm running a Firefox compiled from source and it behaves the same way.

If you can't open by double clicking, then install Firefox again
and run the following commands:

```
sudo mkdir /usr/local/bin
sudo ln -s /usr/lib/swiftfox/swiftfox /usr/local/bin/firefox
```

This will make Swiftfox to be opened whenever you run the firefox command and will allow to open the html desktop links with double clicks.

What version of Firefox you were using before?

I would try to install 3.6.6 from the repositories and apply the ipv6 fix. That will most likely to fix your connection issues.

---

### Post by sandman3838 on 2010-07-10
Hey I'm back!

The Firefox versions I have available are:
Firefox 3.6.8
Firefox 3.7  (Installed)

As you suggested I reinstalled Firefox 3.7 through Synaptic and I ran the CODE you suggested the results were:

keivn@kj-desktop:~$ sudo mkdir /usr/local/bin
[sudo] password for keivn: 
mkdir: cannot create directory `/usr/local/bin': File exists
keivn@kj-desktop:~$ 

With the second line there were no issues:
sudo ln -s /usr/lib/swiftfox/swiftfox /usr/local/bin/firefox

Other information:
I looked for information on disabling IPV6, I used this:

Disable IPv6 in Firefox. Type about:config and search for:
    network.dns.disableIPv6
and set it to TRUE

It was already set to true!

Next I logged out and reentered and tried to drag the link to Google to the desktop what I received is visible on the new attachment.  I tried this with both Firefox and Swiftfox.
What is WEBHP???

Where too now?

---

### Post by lovinglinux on 2010-07-10
> **sandman3838 said:**
> 
Next I logged out and reentered and tried to drag the link to Google to the desktop what I received is visible on the new attachment.  I tried this with both Firefox and Swiftfox.
What is WEBHP???

Where too now?

Can you open the links in Swiftfox by double clicking them?

To fix the problem with dragging from Swiftfox to the desktop try [this](https://addons.mozilla.org/en-US/firefox/addon/66/).

---

### Post by sandman3838 on 2010-07-10
Looks like a partial fix!

Question:
To fix the problem with dragging from Swiftfox to the desktop try this. 

I installed the program you suggested even though it says it was for an earlier version.  Now all those Web link that I have in that folder I have will open to Swift Fox either by Right-Click-Open or by double click.

Question:
Can you open the links in Swiftfox by double clicking them?

The Bookmarks within Firefox/Swiftfox are just fine.
However, if I take a link to the desktop and re-opening them it's mixed?

On the first attempt to copy a Link to the Desktop I get a PHP file copied to the desktop. Next if I try to drag the same link again it works and it will open.

See attachment.

---

### Post by lovinglinux on 2010-07-10
> **sandman3838 said:**
> Question:
Can you open the links in Swiftfox by double clicking them?


Yes.

> **sandman3838 said:**
> The Bookmarks within Firefox/Swiftfox are just fine.
However, if I take a link to the desktop and re-opening them it's mixed?

I haven't tried.

---

### Post by sandman3838 on 2010-07-10
Can you open the links in Swiftfox by double clicking them?

Yes, now they do open to Swiftfox.
But only the OLDER Links that I have in a saved folder on on my desktop.

What still fails is when I try to save a NEW link to the desktop.
What I get... See Attachments.
This was from two different Web sites.

Thank you for all your help.

---

### Post by sandman3838 on 2010-07-11
Got it!

1st I backups my bookmarks.
I went back and I did a total removal from Synaptic.
Next I went and removed the FIREFOX & SWIFTFOX folder remaining in my Home folder.  I just didn't rely on Synaptic.

Rebooted and reinstalled FIREFOX & SWIFTFOX.

Right now all my links are working.

Thanks for all your help Luvinglunix.  You were great.

---

### Post by lovinglinux on 2010-07-11
> **sandman3838 said:**
> Got it!

1st I backups my bookmarks.
I went back and I did a total removal from Synaptic.
Next I went and removed the FIREFOX & SWIFTFOX folder remaining in my Home folder.  I just didn't rely on Synaptic.

Rebooted and reinstalled FIREFOX & SWIFTFOX.

Right now all my links are working.

Thanks for all your help Luvinglunix.  You were great.

You are welcome.

---

### Post by sandman3838 on 2010-07-14
I had some removal and install issued with Firefox and I'm now everything is working with Firefox 366 but the issue with saving to the desktop is back.  And it's a little strange....

As a test there were three Web sites I tried to create a Link to on my desktop.

A.  Ubuntu Forums
B.  Allrecipes.com
C.  Amazon.com

Results:
Ubuntu Forums - 
First try I get a "showthread.php  (1_Attached)
Second try I get a working Link to the site.  (2_In compressed file)

Allrecipes.com - 
First try I get a "default.aspx"   (3_Attached)
Second try I get a working link to the site.  (2_In compressed file)

Amazon.com - 
First and only try I get error message.  (5_Error Msg)

I have also added a screen shot of the icons on the desktop.

---

### Post by lovinglinux on 2010-07-14
> **sandman3838 said:**
> I had some removal and install issued with Firefox and I'm now everything is working with Firefox 366 but the issue with saving to the desktop is back.  And it's a little strange....

As a test there were three Web sites I tried to create a Link to on my desktop.

A.  Ubuntu Forums
B.  Allrecipes.com
C.  Amazon.com

Results:
Ubuntu Forums - 
First try I get a "showthread.php  (1_Attached)
Second try I get a working Link to the site.  (2_In compressed file)

Allrecipes.com - 
First try I get a "default.aspx"   (3_Attached)
Second try I get a working link to the site.  (2_In compressed file)

Amazon.com - 
First and only try I get error message.  (5_Error Msg)

I have also added a screen shot of the icons on the desktop.

I have the same problem. It seems Ubuntu is failing to update the icon name with the url, but it still works properly when you click it. The second time you try the link is already cached or something (I'm guessing), so it creates an icon with the proper name.

BTW, the same happens with Chrome, so is not a Firefox issue.

Have you tried to consider storing bookmarks you don't visit regularly in a different way? I know is not a solution, but maybe we could find a better method to suit your needs.

For example there is [Read It Later](https://addons.mozilla.org/en-US/firefox/addon/7661/) extension that stores bookmarks on a separate database, so you can keep a different set of bookmarks that are not listed in your Firefox bookmarks tree.

What is the main reason you save those bookmarks in your desktop?

---

### Post by sandman3838 on 2010-07-14
Thanks for the info.

Glad to here that it's just not me!  :)
I was thinking about storing the silly things somewhere else as well.
Thanks for "read it Later" program I'll check it out.

KJ

---

### Post by lovinglinux on 2010-07-14
> **sandman3838 said:**
> Thanks for the info.

Glad to here that it's just not me!  :)
I was thinking about storing the silly things somewhere else as well.
Thanks for "read it Later" program I'll check it out.

KJ

There is also [Scrapbook](https://addons.mozilla.org/en-US/firefox/addon/427/), which is basically designed to store complete pages (including html, images and so on) for offline viewing, but can also supper bookmarks (without saving any files). It also allows to create multiple profiles, so the pages files are stored on different folders. Is very customizable.

I think this will be better for your needs.

---

### Post by sandman3838 on 2010-07-14
Hey thanks for the info on scrapbook I'll go and check it out in a minute.

Myself I just found this and it seems to be working.

Save Link In folder
[https://addons.mozilla.org/en-US/firefox/addon/613/%5B/url](https://addons.mozilla.org/en-US/firefox/addon/613/%5B/url)

Here is another one - Link Pad
[https://addons.mozilla.org/en-US/firefox/addon/9706/](https://addons.mozilla.org/en-US/firefox/addon/9706/)

---

### Post by lovinglinux on 2010-07-14
> **sandman3838 said:**
> Hey thanks for the info on scrapbook I'll go and check it out in a minute.

Myself I just found this and it seems to be working.

Save Link In folder
[https://addons.mozilla.org/en-US/firefox/addon/613/%5B/url](https://addons.mozilla.org/en-US/firefox/addon/613/%5B/url)

Here is another one - Link Pad
[https://addons.mozilla.org/en-US/firefox/addon/9706/](https://addons.mozilla.org/en-US/firefox/addon/9706/)

Great.

---

### Post by goltoof on 2010-07-14
personally, I swear by the [delicious]("https://addons.mozilla.org/en-US/firefox/addon/3615/") extension.. I don't trust any OS/browser to save my bookmarks

---

### Post by betlog on 2010-07-22
edit: i dont see how to delete.. so...

---

