---
title: "Run in Terminal not working"
date: 2012-02-24
forum: General Help
---

### Post by craterib on 2012-02-24
Hi,

I am running edubuntu 11.10 with the latest updates. I am not able to use run in terminal command if I try it from nautilus, however it works fine if I try it from terminal.

When I double click it, a white window appears momentarily and then disappears.

Any idea how to solve the problem?

---

### Post by greenpeace on 2012-02-24
hi, 

What command are you running exactly?  Is there any output in the terminal?   copy and paste the lot if you can!

---

### Post by forrestcupp on 2012-02-24
Is it something that doesn't take very long to run? When you double click something that gives you the option to run in the terminal, it doesn't keep the terminal open, but instead, the terminal window closes as soon as the program is finished running. So if it's some script that doesn't take very long to run, then it would be normal for you to see the terminal window flash on the screen and disappear as soon as the script finishes, even if you were expecting some kind of output. 

That's why it's better to just open a terminal and run it from the command line, because the terminal window will stay open that way for you to see the results of what happened.

---

### Post by craterib on 2012-03-01
Hi,

It was just a text file that is supposed to run. When I double click it, "This is an executable file Run in Terminal, Run, Cancel, Display" are the options that appear.

When I press Run in Terminal or Run, a white window appears and then disappears.

However when I run the same file in terminal "./filename" it works without any problem.

This problem occurs only with that file. Other files run normally, both in terminal and in the x-server, (run in terminal option).

I was just curious to know why this anamoly.:confused:

---

### Post by forrestcupp on 2012-03-01
Other text files run normally, though? If all it does is display text without any user input, then it will close immediately after it displays the text, which takes no time at all. 

If you run it in a terminal, is there any user input before it completes, or does it go right back to the command prompt after it displays the text?

---

