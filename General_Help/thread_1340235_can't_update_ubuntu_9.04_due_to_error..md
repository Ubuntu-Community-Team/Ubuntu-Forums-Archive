---
title: "can't update ubuntu 9.04 due to error."
date: 2009-11-28
forum: General Help
---

### Post by hockey97 on 2009-11-28
Hi, I  can see the update manager having about 15 new updates for php,apache,and many more. 

The error I get when I try to update the stupid thing. I would get 
dpkg error lsb -release is missing final new line. 

usr/bin/dpkg returned error 2. 
package failed to install trying to recover. 

I don't know what to do. I even tried selecting one by one the updates and trying to try them one at a time but I get the same exact error. 

I do have lsb -release the latest version of it.

what should I try to do? I need to update the stuff they are security updates for programs and also programming libs for daylight savings time.

any ideas?

---

### Post by pi4r0n on 2009-11-28
[This post]("http://ubuntuforums.org/showthread.php?t=508679") talks about the same issue you go.

Go through it and let us know how did it go.

---

### Post by hockey97 on 2009-12-17
That didn't help....  take a look at my other forum I made about the problem.

here: [http://ubuntuforums.org/showthread.php?p=8516711#post8516711](http://ubuntuforums.org/showthread.php?p=8516711#post8516711)

I have a screen shot of the error message on that page.

I need to get this to work it's driving me crazy. I can't update I can't install any packages.

It's not the update manager but I think the error is from the program that handles installation of .deb packages.

---

### Post by john newbuntu on 2009-12-17
I searched Ubuntu forums and saw a post that had a problem similar to yours:
[http://ubuntuforums.org/showthread.php?t=1319791](http://ubuntuforums.org/showthread.php?t=1319791)
In here, pokerbirch provdes a script to fix this problem.  Essentially, it looks at all files in /var/lib/dpkg/info and add new line to a file that does not have one.

Instead of running this script, my suggestion would be to make a backup of all files in this directory that start with "lsb-release[COLOR=#000000][COLOR=#DD0000][/COLOR][/COLOR]".  Manually edit each of them and add a newline to the end of the file(i.e, go to the end of the last line of each file and hit enter) and save.

If you are a "vi" editor guy, when you do a "sudo vi <filename>", you will get something like "incomplete last line" when you open the file, which means just save the file and the newline will get added.  If you do not use the "vi" editor, ignore this paragraph.

Once this is fixed, rerun your update.  Perhaps even force the installation of lsb-release package.

---

