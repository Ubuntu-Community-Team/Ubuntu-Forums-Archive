---
title: "wget download all starting with..."
date: 2010-02-08
forum: General Help
---

### Post by Wiseman20 on 2010-02-08
I am trying to all files that are specified in the begining ie. ./script p6-8       

I would like to download all of the files that start with that prefix
p6-8_ex{1,2,3}.in/out

Ive been trying  :    $1_ex{1,2,3}.in     but the wget output looks like p6-8_ex%7B1,2,3%7D.in

any help would be great

Thank you

---

### Post by anagor_lv on 2010-02-17
I see, you are writing a script.

As I understand, your problem is a distorted filename. When you download the files from the Internet, the figure brackets are replaced by some other symbols. You want the script to give you correct filenames, when it is executed. Is this right?  

After browsing some forums and sites and trying out some scripting on my computer, I came up with an idea that might help you.

What I think you can do, is add a command line to the script that would rename the files to what they should be named. This is probably the command you need:

```

mv $1_ex%7B1,2,3%7D.in $1_ex\{1,2,3\}.in

```

This command should rename the file p6-8_ex%7B1,2,3%7D.in into p6-8_ex{1,2,3}.in

Did this help you? Please, reply!:)

---

### Post by Wiseman20 on 2010-02-17
i used wget -r -np -nd -A $1* "www.url"

this allowed me to download all the files starting with the parameters entered as inputs. I was unsure of syntax before. Before i was using the brackets to specify i wanted the 3 different files to be downloaded without using 3 wgets. This is a much better implementation for me to use because it will download more or less of what i needed. Thank you for the help, i though this thread would just get burried

---

