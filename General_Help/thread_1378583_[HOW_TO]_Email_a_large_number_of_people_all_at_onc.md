---
title: "[HOW TO] Email a large number of people all at once using Mutt"
date: 2010-01-11
forum: General Help
---

### Post by chaanakya_chiraag on 2010-01-11
Hey guys!  Today I'm going to show you how you can use a program called Mutt to send email to a large group of people all at once.

1) Open up the terminal (Applications -> Accessories -> Terminal) and type in the following command:
```
sudo aptitude install mutt
```  **Note: When/If it asks you for your password, enter YOUR password (it won't show up on the screen) and if it asks you if you want to continue, say yes**.

2) Open up a new Text Editor window (Applications -> Accessories -> Text Editor)

3) Copy the following into the text document (I'll explain it later):
```
#!/bin/bash
echo "Sending emails"
cat "$1" | while read line; do
    echo "Sending email to $line"
    mutt -s "`cat $2`" $line < "$3"
done
```4) Save this as febutimail.sh anywhere you desire.

5) Now for the explanation:
echo "Sending emails": This just outputs "Sending emails" to the terminal window.  It's just for debug/general info purposes.
cat "$1": cat outputs the contents of text files, and we're using the 1st argument ($1) to provide our list of addresses.  So what this does is output the contents of the address list.
|: This **pipes** the output from one command to another.  This means that the command to the right of this symbol will (if it can) use the output supplied by the command to the left of the symbol.
while read line; do: This basically scans the address list one line at a time.  The address list will be formatted with one address per line, so this means it will pass one address at a time to the contents of the while loop.
echo "Sending email to $line": This again just outputs some info.  In this case, it's outputting who it is sending the current email to.  Again, it's just for info purposes.
mutt -s "`cat $2`" $line < "$3": This calls the program mutt (the program you installed earlier), asking it to send a message with the subject of the contents of the second argument (-s "`cat $2`") to the person specified by the line passed to it by the current line from the address list ($line) using the text from the third argument (< "$3").
done: Ends the while loop.

6) Make the script executable by typing ```
chmod +x /path/to/febutimail.sh
``` into a Terminal window.

7) How to set up the address list, subject, and body files:
Address List: This can be named whatever you want, **but it must only have one address per line** for the script to interpret it correctly.
Subject and Body files: Just like a regular document.  No special formatting needed.

ATTENTION: All three files (address list, subject, and body) MUST be plain text.
Also, FYI, you must set up Mutt to use your SMTP server of choice (Gmail, Yahoo! Mail, etc.).  This is outside the scope of this thread and is well documented elsewhere.  A quick Google search should do the trick :)

8) How exactly do I use this thing?
The program should be called as follows:
```
febutimail.sh </path/to/address/list/file> </path/to/subject/file> </path/to/body/file>
```The inspiration for this script came from the Windows-only program febootimail which allows you to send generalized email to a list of people.  Please feel free to comment (good or bad :) ) as well as posting any questions you may have.
- Chiraag

---

