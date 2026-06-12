---
title: "Help needed using shred"
date: 2011-11-27
forum: General Help
---

### Post by unknown user on 2011-11-27
I have a spreadsheet on my desktop in a folder that I need to shred and delete for good. I had a look at a few sites on how to use shred and thought that I had it all figured out. I am working on the Wubi version of Ubuntu, within Windows at the moment. So the file is located in; user 1/desktop/new folder/weekly costs.ods

With this in mind I opened the terminal window and typed the following:

shred -u -z -n 26 user 1/desktop/new folder/weekly costs.ods

I also tried:
shred -u -z -n 26 home/user 1/desktop/new folder/weekly costs.ods
&
shred -u -z -n 26 weekly costs.ods

Each time I got the following error, the file/folder could not be found.

Can anyone help me write the command correct in the terminal window so that I can shred this file please?

Also why has there not been a nice front end created to shred files?

Is shred the best to security delete files, or is there anything better out there?

---

### Post by Habitual on 2011-11-27
Try quotes around "/path/with/spaces/in/file names.ext"
```

shred -u -z -n 26 user "/home/user1/desktop/new folder/weekly costs.ods"

```

---

### Post by unknown user on 2011-11-27
Thanks for that, i sure will try tonight. I was looking at one of the sites that I was looking at last night and with a fresh pair of eyes, I wonder if part of the problem could be due to the fact that I may of missed out the '/' before the word home?

[http://kevin.vanzonneveld.net/techblog/article/delete_files_securely_with_shred/](http://kevin.vanzonneveld.net/techblog/article/delete_files_securely_with_shred/)

---

### Post by unknown user on 2011-11-28
I tried this yesterday and still no joy. May have to move it to a folder on my windows system and use the nice gui secure delete program from there. I was trying all night to try and sort this out without any joy.

Cannot believe that something so easy as deleting a file using shred can create such a time consuming problem!!:confused::confused:

---

### Post by WorMzy on 2011-11-28
File and folder names are case sensitive. Are you sure that you have a "desktop" folder? The default is "Desktop", with a capital D.

Use [tab completion]("https://en.wikipedia.org/wiki/Command_line_completion") if you can't remember the exact file path.

---

### Post by Habitual on 2011-11-28
yes, a missing / on the path is definitely an issue.
Suggest you stick this in your ~/bashrc...IF the "-z -n 26" options are 'normal' for you or that environment. 

```
alias shred="shred -u -z -n 26"
``` 
save and exit ~/.bashrc
```
source ~/.bashrc
```

Then the work is simplified with issuing this:
```
find `pwd` -name "weekly costs.ods" -exec shred {} \;
```

HTH

---

### Post by unknown user on 2011-12-03
Well I think I have sorted this out, so thank you to all the people who have added to this post. The problem as you mentions seemed to be with having the files on the desktop.

I went into one of the folders from my root folder (music) and then clicked Cont and L. That gave me the correct location that I could copy into the terminal command box after the shred line. I tressed return and the file got deleted.

So what I will do now is create a shred folder in my root folder and then always put the files in there that I want to delete for good.

---

