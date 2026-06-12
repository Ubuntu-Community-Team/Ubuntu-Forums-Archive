---
title: "Parse filenames to text output"
date: 2009-12-16
forum: General Help
---

### Post by munkymac on 2009-12-16
A little bit of background:

I run a music website, and every week get hundreds of emails with linked mp3s available for download and posting. Thanks to some other users in the community, I'm able to parse the links in my email folder, output them to a text file, and then use wget to download everything. It's wonderful.

Now, I would like to share those files with my readers. I want to take a selection of mp3s every week, put them in a specified directory, and then point a script at it so the output is properly formatted for HTML, so I can dump it into the HTML view window of our CMS--quick, painless and automated, so I can post once a week with minimum effort.

Here's an example:

File: Mos_Def-Quiet_Dog.mp3

I need the resulting HTML output to be: ```
<a href="/music/Mos_Def-Quiet_Dog.mp3" target="_blank">Mos Def &ndash; &ldquo;Quiet Dog&rdquo; &ndash; [mp3]</a>
```

So that the Text Output on the webpage is: Mos Def &#8211; &#8220;Quiet Dog&#8221; &#8211; [mp3]

So far, I use this string ```
find ./ -name "*.mp3" -print > goldrush.txt
``` to output all the filenames in a specific directory to goldrush.txt. The text file then lists "./Mos_Def-Quiet_Dog.mp3" (i can't find a way to get rid of the './')

I then use this string (which i banged together myself, hence the sloppiness)```
awk '{print "/music/"mp3$""}' goldrush.txt
``` which displays "/music/./Mos_Def-Quiet_Dog.mp3" (in the terminal only, I can't figure out how to get it to print to a new text file)

That's as far as i've gotten. As soon as I try to insert the HTML code, I get syntax errors. 

If anyone can point me in the right direction, or just knows of a good "Command Line Scripting for Dummies" tutorial, I would be highly appreciative. This is my first real CLI work, and I know nothing of scripting.

---

### Post by jm2 on 2009-12-16
I was trying to remove ./ from a file earlier this week. 
I don't have my notes handy, but something like this might work or point you in the right direction:

1. cut -b 1,2 file.txt > output file
man cut (for different option)
-b is byte and 1,2 is remove the 1st 2 bytes of file.txt and put result in output file

or 

2. vi <file>
Esc
You get to the : at the bottom of the screen
s/\./\/s///g <enter>
esc
shift ZZ
(This is vi editing.. look at man vi)


or 

3. Look at sed.  I found a tutorial on the web, and played with it to get what I needed.

---

### Post by john newbuntu on 2009-12-16
A shell script (bash) will be able to achieve what you need to do.  I'll leave the details to you but a skeleton of it would be like:

#!/bin/bash
cd /home/john
IFS='
'
for i in `find . -name "*.mp3" -print`; do
   //perform required manipulations here.
   //echo your final output here.
done

Since you say that you receive hundreds of posts every week, it is almost time to store some of the details from these posts in a database.(say using mysql, which is free) You would then be querying a few fields in the database and displaying the result as html.  The table could have other fields like "user", "date_posted", "active_flag" etc that would help you later on to identify the user, a bad link and will help you in archiving information rather than storing these emails and weeding through them.

---

