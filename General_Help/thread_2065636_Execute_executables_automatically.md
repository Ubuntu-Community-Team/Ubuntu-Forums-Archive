---
title: "Execute executables automatically"
date: 2012-10-02
forum: General Help
---

### Post by aashishsatya on 2012-10-02
Hi,

I've created a small C++ application using Code::Blocks. I've run the program from codeblocks and I've run it using the terminal, and it works fine. But when I click on the executable (that is automatically created by codeblocks in the specified folder), nothing happens. Also, I've copied all the required files to the location where the executable is present. All I want is it to open in the terminal (or in any other console) when I double-click the executable. Is there any way to make this possible?

Thanks and regards,
Aashish

---

### Post by dino99 on 2012-10-02
[http://askubuntu.com/questions/138908/how-to-make-a-script-executable-which-acts-like-exe-files-in-windows](http://askubuntu.com/questions/138908/how-to-make-a-script-executable-which-acts-like-exe-files-in-windows)

---

### Post by aashishsatya on 2012-10-03
Thank you for your prompt reply.
I'm afraid to say that the posted solution hasn't worked for me. 
I forgot to mention that I'm running Ubuntu off a USB with persistence....does it make any difference??
Maybe a step-by-step account of everything I did may help you...
Let's take a sample "hello world" program.

[LIST=1]
[*]I've compiled the helloworld program in Code::Blocks and it runs  fine in the X-Term emulator (I've also added cin.get() at the end so  that it does not exit itself unless the user presses the Enter key)
[*]I go to the folder where I've saved it and I find the executable
[*]I right-click the file, go to Properties and go to the Permissions Tab
[*]I find that "Allow executing file..."**_ has already been checked_**.
[*]I double-click it, and nothing happens.
[*]So, for good measure, I change the "Read Only" in Others>>Access to "Read and Write"
[*]I double-click it, and still nothing happens.
[*]I change it back to "Read Only"
[*]I go to the folder via the Terminal and I give the command chmod ugo+x helloworld
[*]I try double-clicking it - with the same result
[*]I do step 6 again, followed by 9
[*]Still nothing happens when I double - click the file.
[/LIST]
Can somebody tell me what I'm doing wrong??

Regards,
Aashish

---

### Post by Mark Phelps on 2012-10-03
The thread below has examples of commands that will invoke a terminal and THEN run the executable:

[http://www.linuxquestions.org/questions/linux-general-1/run-command-in-new-gnome-terminal-185216/]("http://www.linuxquestions.org/questions/linux-general-1/run-command-in-new-gnome-terminal-185216/")

---

