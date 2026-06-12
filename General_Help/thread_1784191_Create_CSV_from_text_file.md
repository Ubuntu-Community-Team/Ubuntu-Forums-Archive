---
title: "Create CSV from text file"
date: 2011-06-16
forum: General Help
---

### Post by jeremy-nsa on 2011-06-16
Hello,

I have a file like:

a
1
2
b
1
2
c0
1
2
d0a1
1
2

and I would like to convert it to CSV, so that it looks like:
a,1,2
b,1,2
c0,1,2
d0a1,1,2

Basically, I would like to move every 2nd and 3rd line onto the above line, and put a comma to separate

Anyone have any ideas on how I could do this?

Thanks a lot!

---

### Post by nzjethro on 2011-06-16
I'm sure if you can copy the file into a .txt, you should be able to pretty easily write up a Python script to do that for you, if it's all the same format. If you like, I can take a look and see if I can write something to get you started. Otherwise, check out Autohotkey. Not sure if they offer a Linux version, or if there is a Linux clone out there, but it's a macro tool that enables you to set the computer to do repeated menial tasks.

---

### Post by nzjethro on 2011-06-16
I've written a (very) basic Python script that is capable of doing what you requested. If you're interested, post back with the .txt attached or contained within code tags (click the # at the top and post your text in, or else attach the txt file by choosing Manage Attachments below) and I'll run the script and send back the output.

I would send you the code, but I'd prefer not to post code on the Internet, as a few cheeky people post their uni assignment questions here and expect people to write the answers for them. :P

---

### Post by jeremy-nsa on 2011-06-16
Hello,

Thanks for you help. I have PM'd you a sample input.

I am working on importing an old Netware DHCP (DHCP3TAB) server into ISC DHCP. There is no easy way to do this that I have found online, since Netware DHCP3TAB is so old!

Thanks,

---

### Post by kaibob on 2011-06-16
The following will do what you want. If the source file is large, I suspect this is better done with sed or awk. Perhaps another forum member will be able to help if that is the case.  

```

#!/bin/bash

i=1

while read -r line ; do
  case "${i}" in
    1|2 ) printf "%s," "$line" >> newfile.txt ;;
    3   ) printf "%b\n" "$line" >> newfile.txt && i=0 ;;
  esac
  ((i++))
done < file.txt

```

---

### Post by jeremy-nsa on 2011-06-23
Thank you all very much for your help!

---

### Post by couillard45682 on 2011-10-28
How was the import? I'm trying to do the same... can you provide us the import script? Thanks!

> **jeremy-nsa said:**
> Hello,

Thanks for you help. I have PM'd you a sample input.

I am working on importing an old Netware DHCP (DHCP3TAB) server into ISC DHCP. There is no easy way to do this that I have found online, since Netware DHCP3TAB is so old!

Thanks,

---

### Post by jeremy-nsa on 2011-10-28
Hello,

Here is the script I used:



#########################
#CSV programme, created by nzjethro, feel free to edit, use, and distribute, but #not claim as your own.  #Change these directories to your needs. the first one is the file that  #will be read, the second is a file you should create to write to.  read = open ('/home/jethro/practice.txt', 'r') write = open ('/home/jethro/created.txt', 'w')  lines = []  for line in read: 	lines.append(line)  for i in range(0,len(lines)): 	lines[i] = lines[i][:-1] 	 for i in range(0,len(lines)/3): 	write.write(lines[3*i] + "," + lines[3*i+1] + "," + lines[3*i+2] + "\n")

It worked, but I didn't end up using it since my data needed to be cleaned up more. There was the odd case where the input data wasn't /3 so it messed up the sort.

Good luck!

---

### Post by couillard45682 on 2011-10-28
Hi,
Thanks for the quick reply. I'm pretty sure the script you provide me is not the one to convert DHCP3TAB to ISC DHCP? 

> **jeremy-nsa said:**
> Hello,

Here is the script I used:



#########################
#CSV programme, created by nzjethro, feel free to edit, use, and distribute, but #not claim as your own.  #Change these directories to your needs. the first one is the file that  #will be read, the second is a file you should create to write to.  read = open ('/home/jethro/practice.txt', 'r') write = open ('/home/jethro/created.txt', 'w')  lines = []  for line in read: 	lines.append(line)  for i in range(0,len(lines)): 	lines[i] = lines[i][:-1] 	 for i in range(0,len(lines)/3): 	write.write(lines[3*i] + "," + lines[3*i+1] + "," + lines[3*i+2] + "\n")

It worked, but I didn't end up using it since my data needed to be cleaned up more. There was the odd case where the input data wasn't /3 so it messed up the sort.

Good luck!

---

### Post by jeremy-nsa on 2011-10-28
That is correct. This script was a very small portion of the migration process.

---

### Post by couillard45682 on 2011-10-28
and do you still have the complete script?

> **jeremy-nsa said:**
> That is correct. This script was a very small portion of the migration process.

---

