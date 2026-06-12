---
title: "How do you make a .sh batch file in Ubuntu?"
date: 2012-02-23
forum: General Help
---

### Post by Altiris on 2012-02-23
I am having the problem with the Logitech G300 mouse, where every time you click the cursor goes to the top left of the screen.

I found another way to fix this, by going into the terminal and typing: "xinput set-prop 11 121 0" without "" But I have to do this every time I re-boot ubuntu.

I want to know how I can make a batch file so that it opens up the Terminal window and enters in that code. 
(I can set it to start up each boot with the start up programs thingy)

Could anyone make one for me or show me how to do this?

I am on ubuntu 11.10

---

### Post by HeroOfCanton on 2012-02-23
Scripts are very useful in linux and worth learning a bit about. The link below may be a little more than you need for this one task, but in the long run knowing a bit more can really pay off.

[http://tldp.org/LDP/abs/html/index.html](http://tldp.org/LDP/abs/html/index.html)

---

### Post by haqking on 2012-02-23
basics are easy, open a text editor

```
#!/bin/bash  
command 1
command 2
```

save file with .sh extension

simple bash script, (batch file)

---

### Post by forrestcupp on 2012-02-23
Do what haqking said and just put your command after **#!/bin/bash**. Then you'll need to make the file executable by opening a terminal and navigating to the directory you saved the file in, and typing
```
chmod +x ./*filename*
```

Then you can open up Startup Applications and add that script so that it will automatically run every time you start up your computer.

---

### Post by efflandt on 2012-02-23
Besides what the others said, it is best to put any personal scripts or binaries in a **bin** directory in your home directory (ie, ~/bin).  The next time you login, that directory will automatically be in your $PATH, so "you" can simply run scripts in that directory by name from anywhere (except cron) without any path.

---

### Post by evilsoup on 2012-02-23
[Here](http://www.linuxcommand.org) is a website I found quite useful for learning how to write scripts.

In your case, to run that little one-liner at startup, it might be easier to put it in your ~/.profile - that is a script file that is run when you log in. In terminal

```
gedit ~/.profile
```

and then scroll to the bottom of the file and add your bit of script.
I personally prefer this way, but Forestcupp's method will work just as well. Oh! And one more thing: if you are planning on calling scripts that you've made, you'll want to make a bin folder

```
mkdir ~/bin
```

IIRC, Ubuntu adds that to you $PATH automatically. If you had a script normally that you wanted to call, you'd have to type '/path/to/myscript', whereas if your script is in ~/bin, you just have to type 'myscript'.

---

### Post by forrestcupp on 2012-02-24
> **evilsoup said:**
> 
```
gedit ~/.profile
```

and then scroll to the bottom of the file and add your bit of script.
I personally prefer this way, but Forestcupp's method will work just as well.

Nice to know. Thanks.

---

### Post by oldfred on 2012-02-24
My first script was a couple of commands I had run at the terminal and then knew they worked. You can run this command to see the commands you have run.
```

history
```

Then copy the commands into a file with
#!/bin/bash  

After I did that I started following threads and links to undestand how to do more.

---

### Post by cortman on 2012-02-24
And you can get it to run at startup by adding it to your Startup Applications (System Settings>Startup Applications).

---

