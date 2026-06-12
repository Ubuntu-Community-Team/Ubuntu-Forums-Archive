---
title: "notify of finished updates"
date: 2011-12-29
forum: General Help
---

### Post by kaykav on 2011-12-29
HI
  Why doesn't this command finish? :
              sudo apt-get update && date >> ~/file1
     It appears the update part is activated but  no date is put into file1
                                   Thank you

---

### Post by yetiman64 on 2011-12-29
The command you are using is doing an update then (separately) executing the date command and appending (only) the date to the file. If you want to output the update's output to the file as well try,

```
date >> file1 && sudo apt-get update >> file1
```Hope this is of some help.

Edit: just noted your problem being the date not being outputted correctly, your command works perfectly here with regard to just the date.

---

### Post by kaykav on 2011-12-29
yetiman
                     What I want to do is;  Run updates 'then' ,if updates has completed 
                        successfully , put date in a file.  Running it backwards would not give me proof of updates being ran....... without putting the entire updates data
                            in file1.........

---

### Post by yetiman64 on 2011-12-29
> **kaykav said:**
> yetiman
                     What I want to do is;  Run updates 'then' ,if updates has completed 
                        successfully , put date in a file.  Running it backwards would not give me proof of updates being ran....... without putting the entire updates data
                            in file1.........
Ok, I see what you're doing now, I suspect the command you first listed above will do it, copying and pasting your command in terminal works perfectly here (the update runs as per normal in terminal and the date only is put to file1 in the home directory after the update has occurred). 

I would suggest you double check the command you ran earlier from ~/.bash_history (or use the up/down arrows when in the terminal) for any mistyping etc.

---

### Post by kaykav on 2011-12-30
OK    At least  now I know that the form of the command is correct (you ran it successfully). I'll try it again.  Thanks much.....

---

### Post by kaykav on 2011-12-30
Re-did it, but first I removed (unchecked) 3 repository links from synaptic 'third party software',reloaded the repositories, then ran the command again. 'Viola' . The cmd ran fine. Evidently my update procedure was not finishing correctly, so the next cmd 
     (date >>~/file1) did not run...  Persistence paid off.....   Thanks again.

---

### Post by raja.genupula on 2012-05-31
> **kaykav said:**
> HI
  Why doesn't this command finish? :
              sudo apt-get update && date >> ~/file1
     It appears the update part is activated but  no date is put into file1
                                   Thank you
open **sofware center -> History -> updates  **

---

