---
title: "Looping dialog in shell script and saving to file"
date: 2009-11-02
forum: General Help
---

### Post by newtolinux2009 on 2009-11-02
I am trying to input data, using dialog, into a file.
I would appreciate help on
1. how to send the input to a file?
2. how to put it in a loop to get a control on how much data is entered
3. pressing ENTER key terminates the dialog - how can I use ENTER key to function same as DOWN ARROW key
here's the code
 
#!/bin/bash
id=""
name=""
dob=""
 
exec 3>&1
 
VALUES=$(dialog --ok-label "Save" \
--title "Add Records" \
--form "Data Capture" \
15 50 0 \
"Identification No:" 1 1 "$id" 1 10 10 0 \
"name:" 2 1 "$name" 2 10 30 0 \
"Dob:" 3 1 "$dob" 3 10 8 0 \
2>&1 1>&3)
 
exec 3>&-

---

