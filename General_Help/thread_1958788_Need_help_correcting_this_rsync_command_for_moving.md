---
title: "Need help correcting this rsync command for moving files to new Home dir"
date: 2012-04-14
forum: General Help
---

### Post by AlexOnVinyl on 2012-04-14
**UPDATE 4/14/12 7:02PM: found out the issue, but I don't know how to get the right clearance to allow it to copy to the Home folder directly**

Here's the new command: ```
rsync --progress -r /media/ALEXPOULOS/backup/alex/ ~ /home/
```

and here's the output: ```
rsync: recv_generator: mkdir "/home/Music" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
```

----------------------------------------------------------------------------
Original Post:

I recently had an issue with my previous User account - something went wrong and messed up metacity

So, through trouble shooting I've found out that making a new user account - the problem is non-existent in the new account only the old one.

**TL;DR**

- I'm trying to make an rsync command that copies my Home folder to the new one - I backed up my old one to an external drive and am copying from there.

Here's what I have: ```
rsync --progress -r /media/ALEXPOULOS/backup/alex/ ~ /home/alex
```

I let it run for a while and then I realized not only did it back up everything from the my old **BUT also made a dupe folder inside the /home/alex dir also called "alex" which contained all the same files and in turn caused my Hard drive's free space to go from 160GB - 1.5GB** 

So where did I go wrong in this command to have it create a dupe folder?

---

### Post by agillator on 2012-04-14
First, check the ownership and permissions of the directory and/or files, both source and destination, and see if you can determine the problem. If not, try running rsync with sudo (sudo rsync . . . . .). That should copy everything. Then change the owners, groups and permissions as necessary.

---

### Post by papibe on 2012-04-15
Hi AlexOnVinyl.

A few pointers:

(1) The characther ~ represents your home directory. By itself is replaced by the path to your home directory. For example:
```
echo ~
```
should print
```
/home/alex
```

(2) Since there's a space between ~ and /home/alex in your command:
```

...  ~  /home/alex
      ^
```
The /media/.. directory and ~ (your home) are considered sources, thus they bith will be copied on the destination: /home/alex

With all those consideration, try this command:
```
rsync --progress -r /media/ALEXPOULOS/backup/alex/  /home/alex
```
Hope that helps, and tell us how it goes.
Regards.

---

### Post by AlexOnVinyl on 2012-04-16
Solved. Thank you.

---

