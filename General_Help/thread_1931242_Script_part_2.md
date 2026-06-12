---
title: "Script part 2"
date: 2012-02-25
forum: General Help
---

### Post by zergling on 2012-02-25
Hi everyone,
I was wondering if someone could help me out to set up the command below with Zenity and the progress bar.

```

find "${x}" -type f -execdir shred -v -n 1 -u -z '{}' \;

```

After this, the script will be completed and ready to be posted on KDE/Xfce/Gnome Look 

Bye guys and thank you very much :)

---

### Post by Khayyam on 2012-02-25
> **zergling said:**
> I was wondering if someone could help me out to set up the command below with Zenity and the progress bar.

```

find "${x}" -type f -execdir shred -v -n 1 -u -z '{}' \;

```

Firstly, what is variable ${x} ... I assume you mean ${1}

The following (untested) should give you some idea of how to go about creating a progress dialog ...

Note 1: I'm only vaguely familiar with zenity, so please test this with a less potentially dangerous command (ie "echo 1 > /dev/null ; sleep 5").

Note 2: I've left variable "${x}", its probably empty and so find will no doubt error. If you replace it with ${1} then, test with a less potentally dangerous command. 

```
#!/bin/bash

zenity --question \
--text=&#8221;Are you sure you want to shred all files in ${x}?&#8221;

ans=$?

if [["${ans}" == "1" ]]; then
    exit 1
fi

find "${x}" -type f -execdir shred -v -n 1 -u -z '{}' \; 2>&1 | \
zenity --progress \
--title="Shredding in Progress!" \
--text="Shredding..." \
--percentage=0 \
--auto-close \
--auto-kill 

if [[ "$?" = -1 ]]; then
    zenity --error \
    --text="Shredding canceled."
else
    zenity --info \
    --title="Shredding completed"
    --text="The shredding of ${x} is complete."
fi
```HTH ... khay

---

### Post by zergling on 2012-02-25
Hi Khay,
Thank you a lot for all your help :)

The ${x} is where I store the input selection

I have tried the code that you provided me but the progression bar is not increasing during the shredding :(

This is the code that I have so far
```

#!/bin/bash

x=$(zenity --file-selection --directory)

if [[ -z ${x} ]]; then
    zenity --info --text "No parameters given. Program Terminated!"
    exit
fi

zenity --question --text "Are you sure you want to Shred $x?"

case "$?" in
     0) zenity --question --text "\nYou will lose these files/dirs forever!!!"
        if [ $? -eq 0 ]; then
           find "${x}" -type f -execdir shred -v -n 1 -u -z '{}' \; 2>&1 | \
                    zenity --progress \
                           --title="Shredding in Progress!" \
                           --text="Shredding..." \
                           --percentage=0 \
                           --auto-close \
                           --auto-kill 

                            if [[ "$?" = -1 ]]; then
                               zenity --error \
                                      --text="Shredding canceled."
                            else
                               zenity --info \
                                      --text "$x \n\nHas been shredded"
                                      --title="Shredding completed"
                            fi 
           rm -frv "${x}"
        else
           zenity --info --text "Program Terminated..."
        fi
     ;;

     1) zenity --info --text "Nothing has been Shredded"
     ;;
esac

```

By using ```
 rm -frv "${x}" 
``` I can now remove also folder with spaces :P 



Everyone is very WELCOME to help me and improve this script so that I can share it with the Linux community ;)
Ciao a tutti ):P


P.S. If you would like to try this script the "safe" way is to create a new folder and place in it some random files and use the script on it.

---

### Post by Khayyam on 2012-02-25
> **zergling said:**
> Hi Khay, Thank you a lot for all your help

Your welcome ...

> **zergling said:**
> The ${x} is where I store the input selection

I see, well you might have posted the code (paricularly the --file-selection) as then I wouldn't have written the tests they way I did.

> **zergling said:**
> I have tried the code that you provided me but the progression bar is not increasing during the shredding

Yes, probably as my example used "--autoclose" and "--kill", which probably won't work with checking exit status at the end. So, please try the following:

```
#!/bin/bash

x=$(zenity --file-selection --directory)

if [[ -z ${x} ]]; then
    zenity --info --text "No parameters given. Program Terminated!"
    exit
fi

case "$?" in
    0) zenity --question --text "\nYou will lose these files/dirs forever!!!"
        if [ $? -eq 0 ]; then
            find "${x}" -type f -execdir shred -v -n 1 -u -z '{}' \; 2>&1 | \
            zenity --progress \
            --title="Shredding in Progress!" \
            --text="Shredding..." \
            --auto-close \
            --auto-kill &&
            rm -fr "${x}"
        else
            zenity --info --text "Program Terminated..."
        fi
    ;;
    1) zenity --info --text "Nothing has been Shredded"
    ;;
esac
```I'm not 100% sure it'll work as expected, but from the examples I've read this is how you provide a 'progress'. The example from [Gnome Library]("http://library.gnome.org/users/zenity/stable/zenity-progress-options.html.en") states that you should set it to the "initial percentage", ie "0", but wouldn't that **always** be zero, odd. Other examples I've seen don't use "--percentage" so I've removed it from the above.

> **zergling said:**
> By using 'rm -frv "${x}"' I can now remove also folder with spaces

Yes, because the "" (double quotes) protect spaces. BTW, the "-v" (verbose) switch is un-necessary, the output goes nowhere (removed from above).

HTH ... khay

---

### Post by zergling on 2012-02-25
Hi Khay,
The script is not working....
Last night I was thinking that maybe we need to count the #files and based on it, we can update the progression bar.
So, with this in mind, I started looking around and I found this

```
#!/bin/bash

#shredding! for use with nautilus-actions (option %M)
zenity --question --text='Shred the select files?' --ok-label=Shred --cancel-label=Cancel
if [ $? == 0 ]; then
    count=0
    total=$#
    (while [ -n "$1" ]; do
        echo $((100*$count/$total))
        shred -xuz "$1" > /dev/null
        #one increment per file, could do it by size instead (roughly proportional to shredding time)
        count=$(($count+1))
        shift
     done
     echo 100
    ) | zenity --progress --auto-close --auto-kill --text="Shredding..."
fi
```

Is not working corretly for what I saw, but it implements what I had in mind.

Everyone is WELCOME to help me and Kahy with this :)

Ciao

---

### Post by Khayyam on 2012-02-26
> **zergling said:**
> The script is not working.... Last night I was thinking that maybe we need to count the #files and based on it, we can update the progression bar.

Hmmmmm ... we'll I'm not sure progession on "file" count will help as ${1} can be anything, and so with the above script we might end up passing directories to shred, which wouldn't work as shred only accepts files as a target. This was the whole purpose of using 'find -type f'.

When you say "not working" do you mean there is no progess bar whatsoever? It may be that with few files as input the progress is too fast to be noticed. Does the shredding occur, and is ${x} removed? The problem may be that with little data to shred it all happens too fast to provide any noticable "progress". Similarly with file count, if it only has one or two files as input then "progress" would be too fast to notice.

The idea of a progress bar would be for tasks that in effect take some noticable time, downloads for instance. Other than this I can't see what the issue would be with what I posted previously. Please test again with a file of some size (say > 30MB), otherwise please provide more info on how its "not working".

best ... khay

---

### Post by zergling on 2012-02-27
Hi,
With "not working" I mean that the progress bar does not increases. It just start from 0% and goes straight to 100% once everything is done. In other words, is not increasing based on the amount of the job done.

I think that to make my life easier, I could just display the progression via xterm...

---

### Post by Khayyam on 2012-02-28
> **zergling said:**
> With "not working" I mean that the progress bar does not increases. It just start from 0% and goes straight to 100% once everything is done. In other words, is not increasing based on the amount of the job done. I think that to make my life easier, I could just display the progression via xterm.

OK, well, what amount of data was used? The time it takes to go from 1mb to 0mb is probbaly less then the time it takes to calculate how long the the task will take. 

I'm not sure how zentiy does this as all we are doing is providing stdout from the command, but in all the examples I've seen this seems to be method used. Anyhow, unless shred provides somekind of counter any attempt at calculating the exact time the process will take and then graphing that to a meter may be futile.

I'm not sure what else to suggest ... sorry ... khay

---

### Post by zergling on 2012-02-28
Hi Khay,
Do not worry about it. At this point I will just show an xterm windows :)
Thank you Khay.

---

