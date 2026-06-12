---
title: "Moving from Evolution to Thunderbird"
date: 2012-05-25
forum: General Help
---

### Post by asharpham on 2012-05-25
I want to change over to Thunderbird for email handling and have several hundred emails I want to keep. These are in Evolution so I want to export them to Thunderbird.

I checked the instructions on page:
[COLOR=Blue]https://support.mozillamessaging.com/en-US/kb/switching-thunderbird?s=import+messages+from+evolution&as=s#w_importing-evolution-messages[/COLOR]
and tried to follow the steps.

Getting to the folders wasn't too hard but I don't quite understand the instruction that tells me to copy the files (folders I presume) "into the emplacement used by Thunderbird". What do they mean by "emplacement"?

Do empty folders with equivalent names need to exist in Thunderbird first?

In Thunderbird, all the emails have gone into a folder named "cur" and are not displayed correctly.

I'd appreciate some guidance as I'm obviously doing something wrong.

Alan.

---

### Post by phaed on 2012-05-25
It looks like that guide was written by a non-native English speaker. By "emplacement" I think they just mean "place".

Basically, copy the files without extensions (Inbox, Outbox) from 

~/.local/share/evolution/mail/local

to

~/.thunderbird/<profile name>/Mail/Local Folders

---

### Post by asharpham on 2012-05-25
In theory this should be easy. However, it's just not working. I copy the relevant folders (although Evolution doesn't contain an Inbox folder - Weird as there is definitely an Inbox when I open Evolution), and paste them into Thunderbird but the mail contained in them just doesn't show up. The folders don't seem to create where I expect them to be.

Also, the folders in Thunderbird have 3 sub folders: "cur", "new" and "tmp". Where do these fit in? They're not mentioned in the instructions.

Alan.

---

### Post by asharpham on 2012-05-29
I've started using Thunderbird despite the fact that I can't import the mail from evolution. However, there are dozens of files in the "cur" folder in Thunderbird with odd names like "1318684170.2046_4.alan-dell:2,S". I suspect these are the mail from Evolution but the files don't display.

Is there some way of displaying these files?

Alan.

---

### Post by Zill on 2012-05-29
asharpham:  You haven't said which version of Evolution you are using but if it is v3.2.0 or later then the link you have provided is not appropriate.  The later versions of Evolution use the maildir format, as opposed to the mbox format used by earlier versions of Evolution.

See the Evolution section of [Importing and exporting your mail]("http://kb.mozillazine.org/Importing_and_exporting_your_mail") for specific information on how to import maildir format files.

---

### Post by asharpham on 2012-07-03
Unfortunately none of the answers have helped me open these files and the insructions on pages suggested by Zill haven't helped either.  Any other suggestions? By the way, the version of Evolution I was using is 3.2.3 .

Alan

---

### Post by asharpham on 2012-07-03
Bump!

---

### Post by Zill on 2012-07-03
> **asharpham said:**
> Unfortunately none of the answers have helped me open these files and the insructions on pages suggested by Zill haven't helped either.  Any other suggestions? By the way, the version of Evolution I was using is 3.2.3 .
Please don't "bump" a thread immediately!  It is standard practice to wait at least 24 hours before bumping a thread.  As it is over a month since your last post in this thread I fail to see the urgency!

When you say the instructions I provided haven't helped can you please be more specific.
> Evolution 3.2.0 and later uses maildir files. If you created your Evolution profile using a version that defaulted to maildir you will need to use a tool to convert maildir files into mbox files for multiple folders, such as maildirarc or maildir2mbox. Then you can import the mbox files using the ImportExportTools add-on, and resume using the article for how to import your other data.
Did you use maildirrc *or* maildir2mbox to convert your maildir files to mbox format?

Did you install the ImportExportTools into Thunderbird?

Please advise more details of what, exactly, you did and how it failed, with error messages if appropriate.

---

### Post by cforput on 2012-07-05
I'm trying to use maildir2mbox but when I run it I get the following error: 

The program 'maildir2mbox' is currently not installed. You can install it by typing: sudo apt-get install qmail

I'm trying to convert evolution to thunderbird and don't use qmail. I am also executing this in terminal from the folder that contains the file. Lastly, I checked the permissions and the flag to Allow executing file as a program is checked.

Any ideas?

---

### Post by Zill on 2012-07-05
> **cforput said:**
> ...The program 'maildir2mbox' is currently not installed...
Caveat:  I use an earlier version of Evolution that uses mbox files and so unfortunately I don't have any maildir files to test this with.

Looking at "maildir2mbox" from [https://github.com/jooooooon/maildir2mbox]("https://github.com/jooooooon/maildir2mbox") this seems to contain two scripts and a README file, rather than a program.  When you download and unzip this file the README states:
> Usage
=====

cd /path/to/your/source/maildir
maildir2mbox > /path/to/your/destination.mbox

[COLOR="Red"]Note: you must make sure that the path to the accompanying script "dateRfc3339ToMbox.pl" is correct in the maildir2mbox script.[/COLOR]
Looking at the maildir2mbox script, it seems to me that you should edit line 42 to change the path to the location you have unzipped file "dateRfc3339ToMbox.pl" to.  e.g.
```
DATE=$([COLOR="Red"]/root/scripts[/COLOR]/dateRfc3339ToMbox.pl "$DATE")
```
edit to show
```
DATE=$([COLOR="Red"]my path to[/COLOR]/dateRfc3339ToMbox.pl "$DATE")
```
HTH.

---

### Post by sterilegenie on 2012-07-05
Why dont you send all of the emails you would like to keep to a different email account and then send them back to the account you have setup with thunderbird?

---

### Post by asharpham on 2012-07-09
The version of Evloution I was using is 3.2.3. It doesn't have an export function in the "File" menu. I was not aware that the evolution emails were not mbox files. I'd like to try maildir2mbox but I'm not confident I can edit the script correctly. How easy is it to find the path to the maildir files?

By the way, i have many dozens of emails I'd like to save so sending them to another email address and then back is not an option for me unless I can't make anything else work. Besides, working through this is a part of my linux education.

---

### Post by cforput on 2012-07-12
Changing the scropt is really easy. You only need to change line 42 to have it point to where the script is stored on your computer. The only issue I had it that the first place I put the maildir2mbox script was in a folder that wouldn't execute scripts. I don't know much about linux and don't know why thta happened but after I moved it to the usr/local/bin folder it worked fine. You do get lots of errors but my email seemed to convert. I literally had over 5000 emails I converted.

---

### Post by asharpham on 2012-07-17
I'm still battling with this. I don't really understand how to implement some of these suggestions, especially when told to run a script. Where do I run it from and what do I call it?

For example, I came across a script on this page:
[https://github.com/jooooooon/maildir2mbox/blob/master/maildir2mbox](https://github.com/jooooooon/maildir2mbox/blob/master/maildir2mbox)

I can copy and paste it, but where to, and what do I call it so I can run it?

---

### Post by Zill on 2012-07-18
> **asharpham said:**
> I'm still battling with this. I don't really understand how to implement some of these suggestions, especially when told to run a script. Where do I run it from and what do I call it?
Scripts are very widely used and so I suggest you read-up on how to use them:

[INDENT][ScriptingHowto]("https://help.ubuntu.com/community/AdvancedCommandlineHowto#Scripting")
[The Beginner&#8217;s Guide to Shell Scripting]("http://www.howtogeek.com/?post_type=post&p=67469")[/INDENT]

The most important thing to note is that you *must* make the script executable with the chmod command (or via the Nautilus GUI).

You can call the script anything you like but when you run the script you should be in the same directory, otherwise you may have problems with the path to the file.

You generally run a script with the "./" prefix to the filename:
```
./mygreatscript
```
> **asharpham said:**
> For example, I came across a script on this page:
[https://github.com/jooooooon/maildir2mbox/blob/master/maildir2mbox](https://github.com/jooooooon/maildir2mbox/blob/master/maildir2mbox)

I can copy and paste it, but where to, and what do I call it so I can run it?
Your link showed the contents of a single file, maildir2mbox.  Instead, I suggest you should open this link:  [https://github.com/jooooooon/maildir2mbox]("https://github.com/jooooooon/maildir2mbox")
You will see *three* files listed, together with a "ZIP" button near the top.  If you click on the "ZIP" button, this will allow you to download all three files together in one package.

Unzip (Extract) the file to a location of your choice, then you should see a folder containing the three files.

Edit file "dateRfc3339ToMbox.pl" as described in the README and in my earlier post [#10]("http://ubuntuforums.org/showpost.php?p=12078217&postcount=10").

Then run the script "maildir2mbox" as described in the "Usage" section of the README file.  Note that if the scripts are in your path then you may not need to use the "./" prefix but if they are *not* included in your path then just try adding the "./" prefix.  i.e.
```
cd /path/to/your/source/maildir
[COLOR="Red"]./[/COLOR]maildir2mbox > /path/to/your/destination.mbox
```

p.s.  Prior to running the scripts don't forget to make both scripts executable as mentioned earlier. ;-)

---

