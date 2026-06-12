---
title: "Help with a bash script"
date: 2010-04-14
forum: General Help
---

### Post by ardchoille42 on 2010-04-14
I have written the following bash script for a friend to add as a menu item and would like some input on it:

```
#!/bin/bash
# Filename: browseropen.sh
# Version: 0.1
# Date: April 13, 2010
# Author: Ian MacGregor (aka ardchoille)
# License: GPL
# Requires: firefox, zenity
# Description: This script opens a user-supplied URL in the firefox web browser

myurl=`zenity --entry --title="Firefox - Open Webpage" --text="Please enter a URL:" --entry-text ""`

# The zenity text entry dialog consist of “ok” and “cancel” buttons.
# When user clicks “ok” it returns 0, “cancel” returns 1.

# If user clicks the "cancel" button
if [ $? == 1 ]
then
	exit 1
# If user clicks the "ok" button and text box is empty
elif [ -z $myurl ]
then
	exit 1
fi

# Open the specified URL in a new tab if firefox is running.
# Otherwise open in a new instance of firefox.
firefox -new-tab $myurl

exit
```

The script works correctly, I was just wondering if the syntax is correct or if it would cause any unforeseen problems.

---

### Post by prodigy_ on 2010-04-14
Looks alright to me. ```
[ -z $myurl ]
``` is technically wrong but won't cause any problems.

---

### Post by ardchoille42 on 2010-04-14
> **prodigy_ said:**
> Looks alright to me. ```
[ -z $myurl ]
``` is technically wrong but won't cause any problems.

How would I change that to be technically correct?

---

### Post by prodigy_ on 2010-04-14
> **ardchoille42 said:**
> How would I change that to be technically correct?
Just use double quotes. Like: ```
[ -z "$foo" ]
```
Again, in case of **test -z** it doesn't really matter. I say it's wrong only because it may easily lead to wrong assumptions. For example ```
[ -n $foo ]
``` returns "true" if **$foo** isn't defined at all. Not quite as expected, eh?

---

### Post by ardchoille42 on 2010-04-14
> **prodigy_ said:**
> Just use double quotes. Like: ```
[ -z "$foo" ]
```
Again, in case of **test -z** it doesn't really matter. I say it's wrong only because it may easily lead to wrong assumptions. For example ```
[ -n $foo ]
``` returns "true" if **$foo** isn't defined at all. Not quite as expected, eh?

Very good point, I'll use double quotes. Thank you very much.

---

### Post by rnerwein on 2010-04-14
hi 
i think what you want is to insert a command or something else ?
that's the way it works:
#!/bin/bash
#
command=`zenity  --title "run a command" --entry --text "give me the command" --width 1000 --height 50`
firefox -new-tab $command
exit 0

have fun
ciao

---

### Post by ardchoille42 on 2010-04-14
> **rnerwein said:**
> hi 
i think what you want is to insert a command or something else ?
that's the way it works:
#!/bin/bash
#
command=`zenity  --title "run a command" --entry --text "give me the command" --width 1000 --height 50`
firefox -new-tab $command
exit 0

have fun
ciao

The name of the variable doesn't really matter, I was just worried about error checking, which is why there is so much more code in my script. What if the user doesn't enter anything but hits the OK button anyway? What if the user hits the Cancel button? With your code, a new firefox window opens if the user doesn't specify a URL or hits the cancel button, and that's what I was trying to alleviate. Or did I misunderstand your post?

---

### Post by kaibob on 2010-04-14
> **ardchoille42 said:**
> 
The script works correctly, I was just wondering if the syntax is correct or if it would cause any unforeseen problems.

To be technically correct, I think [ $? == 1 ] should be [ $? -eq 1 ] because it is integer comparison.

---

### Post by ardchoille42 on 2010-04-14
> **kaibob said:**
> To be technically correct, I think [ $? == 1 ] should be [ $? -eq 1 ] because it is integer comparison.

That works, I'll make that change.. thanks!

---

