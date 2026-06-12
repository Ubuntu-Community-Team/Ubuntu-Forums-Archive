---
title: "Running shell scripts with App Launcher"
date: 2009-10-09
forum: General Help
---

### Post by nCryp7 on 2009-10-09
So, I've just installed Storybook which is awesome. I can only run it from command line by going into the directory and typing...

./storybook.sh

I'm trying to put a custom launcher on my panel, and tried (with no success) to set the command to...

/home/ncrypt/Storybook/./storybook.sh

Didn't really expect it to work and obviously it did not. So, I'm wondering what command I need to use to run the shell script from the custom app launcher? Or really any way to make this more convenient than running from a terminal every time.

Thanks!

---

### Post by deconectat on 2009-10-09
/home/ncrypt/Storybook/storybook.sh

---

### Post by wojox on 2009-10-09
When you get to Command Browse for the script. You may also need to set the type to Application in Terminal.

---

### Post by nCryp7 on 2009-10-09
Thanks for the quick replies, tried setting it to launch in a terminal with the provided command (/home/ncrypt/Storybook/storybook.sh) but all I get is a really quick flash of the terminal and then it disappears and nothing happens.

---

### Post by EamonSloane on 2009-10-16
yes, I am having this same problem.  I've tried every variation that I can think of:
sh /home/username/directoryname/scriptname.sh
/home/username/directoryname/scriptname.sh
./home/username/directoryname/scriptname.sh
I've made the script executable, I've even tried writing another script which runs that script and that does the same thing (I'm not really sure what I was expecting to happen...).
I've tried "Application" and "Application in Terminal" for all three of those.
I've tried putting quotes around the path like the launcher does when you use the Browse button.

the weird thing is that I can run it from the terminal simply by typing "~/directoryname/scriptname.sh", no ./ or sh or even navigating to the relevant directory

some of those options give me an "error creating child process", some of them just flash the terminal and do nothing, some of them just do nothing...

---

### Post by nCryp7 on 2009-10-17
> **EamonSloane said:**
> yes, I am having this same problem.  I've tried every variation that I can think of:
sh /home/username/directoryname/scriptname.sh
/home/username/directoryname/scriptname.sh
./home/username/directoryname/scriptname.sh
I've made the script executable, I've even tried writing another script which runs that script and that does the same thing (I'm not really sure what I was expecting to happen...).
I've tried "Application" and "Application in Terminal" for all three of those.
I've tried putting quotes around the path like the launcher does when you use the Browse button.

the weird thing is that I can run it from the terminal simply by typing "~/directoryname/scriptname.sh", no ./ or sh or even navigating to the relevant directory

some of those options give me an "error creating child process", some of them just flash the terminal and do nothing, some of them just do nothing...
Ya I've looked all over the place, tried every variation I could think of, no results so I just gave up :\
I'm kinda shocked that there is no simple solution to what I thought at first was an issue of ignorance, but in my search for information I just can't find any leads other than the ones I've already tried.

---

### Post by GodBane on 2009-10-26
sh /home/ncrypt/Storybook/storybook.sh

Should work.
Make sure it's executable.
Make sure the directory is spelled correctly.

---

### Post by nCryp7 on 2009-10-26
Yep, tried sh too with no luck

Upon rechecking my permissions and such to make sure it was set as an executable, I saw that the default under "Open With" was Wine for some reason, so I tried replacing that with both the sh command and gnome-terminal, neither of them worked; I just don't get it. I either get nothing at all or I get a flash of the terminal that's gone before it's completely drawn on the screen.

- EDIT -

BTW It was indeed set to executable and the directory is correct

---

### Post by undecim on 2009-10-26
try the command ```
bash -c "/home/ncrypt/Storybook/storybook.sh; read"
```
That way, the terminal should at least stay up long enough for you to see what it said.

---

### Post by jswhite on 2009-11-02
Had the exact same problem with Storybook. Here's how I solved it.

Make your custom application launcher, targeted at "/home/ncrypt/Storybook/storybook.sh", or wherever your Storybook directory is. Type "Application" is fine; it does not need to run in the terminal. But it will work either way.

Go to your storybook directory in Nautilus, right click on "storybook.sh" and open it with gedit (or otherwise open it with your text editor of choice).

The contents of the original shell script should be as follows:
```

#!/bin/bash

echo "starting ..."
java -Xmx192m -jar lib/storybook.jar
echo "done."

```

Change it to this:
```

#!/bin/bash

cd /home/ncrypt/Storybook
java -Xmx192m -jar lib/storybook.jar

```

The "echo" lines are superfluous. They're only for giving you some updates in bash if you launch it through the terminal. Since you're not, you don't need them. By adding the "cd" command before you run it, you change the directory you're working in with the "java" command to your Storybook directory. If you don't do that, it will be looking in the wrong place for the .jar files associated with Storybook.

That's what worked for me.

---

### Post by souravjha on 2010-04-11
I have a slightly different problem.
I am able to call a shell i have created from the app launcher on the panel. This shell is supposed to take inputs from the user. It takes inputs if I run it from terminal using the command
sh Sync.ksh
but when I use the same command in Custom Application Launcher
sh /home/sourav/Sync.ksh
it does not ask for user inputs.

Please find the shell below:

echo "Do you need to Sync the folder? (y/n)"
read answer
if [ $answer = 'y' ]; then
echo "Sync in progress..."
<perl script>
echo "Sync complete"
fi
/opt/google/chrome/google-chrome <html file> %U
exit;

Please help.
Thanks.

---

### Post by souravjha on 2010-04-18
if anyone could respond to this please :(

---

### Post by Apostle_Monkey on 2010-10-15
To make a shell script run straight from the App launcher you need to:

First create your script - /home/user/script.sh

Make you script executable, open a terminal:
:~$cd /home/user
:~$sudo chmod +x script.sh

You can now drag and drop the shell script onto the App launcher or You can right click it, select 'Add to Panel...' then select Application Launcher.

You will now have the 'Create Launcher' window open:

First select Type - 'Application in Terminal'
Then give it a relevant Name and Comment.

And finally the bit you have all been waiting for, the Command:

sh "/home/user/script.sh"

Note: This is how it should be entered into the dialogue box including the quotes.

Hope this is of use to you guys (and gals)

---

