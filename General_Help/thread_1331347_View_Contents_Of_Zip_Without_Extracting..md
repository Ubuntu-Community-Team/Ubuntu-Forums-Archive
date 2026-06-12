---
title: "View Contents Of Zip Without Extracting."
date: 2009-11-19
forum: General Help
---

### Post by CodeLab on 2009-11-19
Hi...
I Want To Do This Via Command Line

I Wish To View Contents Of Zip File Without Extracting..
I Know Command For It Is
unzip -l filename.zip

But It Is Not Complete
With Above Command I Get This

[FONT=Courier New][COLOR=Sienna]Length [/COLOR][/FONT][FONT=Courier New][COLOR=DarkOliveGreen]Date[/COLOR][/FONT][FONT=Courier New][COLOR=DarkSlateBlue]  Time [/COLOR][/FONT][FONT=Courier New][COLOR=Indigo][COLOR=Red]Name[/COLOR][/COLOR][/FONT][FONT=Courier New]
 --------    ----       ----     ----
[/FONT]      [FONT=Courier New][COLOR=Sienna]2796 [/COLOR][/FONT][FONT=Courier New][COLOR=DarkGreen]00-00-80[/COLOR][/FONT][FONT=Courier New][COLOR=DarkSlateBlue] 00:00[/COLOR][/FONT][FONT=Courier New][COLOR=Red] file1.txt[/COLOR][/FONT][FONT=Courier New]
[/FONT]    [FONT=Courier New][COLOR=Sienna]541922[/COLOR][/FONT][FONT=Courier New][COLOR=DarkGreen] 00-00-80 [/COLOR][/FONT][FONT=Courier New][COLOR=DarkSlateBlue]00:00[/COLOR][/FONT][FONT=Courier New][COLOR=Red] file2.txt[/COLOR][/FONT][FONT=Courier New]
[/FONT]         [FONT=Courier New][COLOR=Sienna]0[/COLOR][/FONT][FONT=Courier New][COLOR=DarkGreen] 00-00-80[/COLOR][/FONT][FONT=Courier New][COLOR=DarkSlateBlue] 00:00[/COLOR][/FONT][FONT=Courier New][COLOR=Red]  folder1/[/COLOR][/FONT][FONT=Courier New]
 --------                   -------
   544718                   3 files[/FONT]

Now, I Want To View Contents Inside folder1/ Also...

Is That Possible ?


Also, In Case Its Not Possible To View Contents Of folder1/ Then,
How Do I Extract Contents Of Only folder1/
Without Extracting Whole Archive...

---

### Post by ghostborg on 2009-11-19
Hi ,
Not an expert just thought I would test it out on my system and give you feedback.
I grabbed a random zip file that had sub folders and just entered unzip -l filename.zip and it showed everything including the sub folders and files within. At first I thought i might need to add -v verbose but just the -l showed everything. I don't know why yours did not. The version of unzip on my Ubuntu 9.10 Karmic is UnZip 6.00 of 20 April 2009.
Did you inspect your zip file with the Archive Manager to make sure your sub folder actually has files in it, might not have been added for some reason when it was packed.
Good Luck

---

### Post by CodeLab on 2009-11-19
Hi Ghostborg
Thanks For Reply

Mine Does Not Works As Yours..
I Verified Subfolder Has Files, But I Cant Get Them Listed

Also, Can You Answer This...
If I Want To Extract Only 1 Folder From Archive How Do I Do It...

Reason, Archives Are Too Big, Several 100s Of MBs, But I Want 1-2 Specific Folders/Files From Each Archive... I Cant Extract Whole Archive To Obtain Only 1-2 File/Folder

Also, To Let You Know, I Am Remotely Connected To Ubuntu Server Via SSH...
I Am Not On Ubuntu Desktop...
Dont Even Know Commands To Check Versions And Stuff...

Hope, This Post Is Not In A Wrong Section...

---

### Post by falconindy on 2009-11-19
"lesspipe" will do what you ask. After installing, it gives 'less' the ability to view the contents of compressed files. For example:
```
 [haruko@quake ~/dev/git/aur]$ less deluge-svn.tar.gz 
==> use tar_file:contained_file to view a file in the archive
drwxr-xr-x haruko/haruko     0 2009-11-17 14:38 deluge-svn/
-rw-r--r-- haruko/haruko  1166 2009-11-17 08:44 deluge-svn/PKGBUILD
-rw-r--r-- haruko/haruko   333 2009-11-17 09:06 deluge-svn/deluge.install
deluge-svn.tar.gz (END)
```

---

### Post by CodeLab on 2009-11-19
Hi falconindy
I Am Not An Expert
What You Said Didn't Made Much Sense To Me

I Tried, lesspipe filename.zip
less filename.zip

Neither Worked...
As Said, I Am Remotely Connected To ubuntu Server Via SSH
I Cannot Install "Lesspipe" (If It Needs To Be Installed) Without Permission Of Server Admin

Again, 1 Question Is not Answered..
How Do I Extract Only 1 Folder From Zip Archive

Say From Archive today.zip
I Want To Extract Only 1 Folder Named images/

---

### Post by CodeLab on 2009-11-20
Hi Ghostborg

I Dont Know What Changed Since Yesterday, But Now
unzip -l filename.zip Works As You Said It Works For You,
Listing All Archive File Names, Including Files Inside Sub-Folders

If Anyone Can Please Answer This,
How Do I Extract Only Required File From A Zip Archive

Say From today.zip I Want To Extract
/images/image1.jpg

I Dont Want To Extract Whole Archive, But Only /images/image1.jpg

---

### Post by CodeLab on 2009-11-20
Ok I Got It...
Its Like This

unzip today.zip images/image1.jpg

Or It Can Also Be Like This
unzip today.zip images/image1.jpg images/image2.jpg images/image3.jpg .... (And So On)

Thanks Ghostborg And Falconindy For Your Help

Peace Out

---

