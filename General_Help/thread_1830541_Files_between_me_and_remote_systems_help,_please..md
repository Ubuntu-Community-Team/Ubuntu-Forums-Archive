---
title: "Files between me and remote systems help, please."
date: 2011-08-21
forum: General Help
---

### Post by MutantJohn on 2011-08-21
Hello All,

So, I finally got an account on one of my school's computers and I need to transfer some files on my computer to theirs. I'll so my little ssh to get in and I know that the cp command copies files and I heard that if I want to copy a folder full of stuff the command was cp -r, right? 

Anywho, I don't actually know the paste command. Or actually, I don't even know if this is what I need to be doing.

Basically, how do I transfer files from my computer to theirs? I don't know if it matters but yes, both computers are linux.

Thanks in advance.

---

### Post by Habitual on 2011-08-21
rsync is my suggestion.

[http://www.thegeekstuff.com/2010/09/rsync-command-examples/](http://www.thegeekstuff.com/2010/09/rsync-command-examples/)

"Example 4. Synchronize Files From Local to Remote"

---

### Post by 3Miro on 2011-08-21
Assuming you are using a Ubuntu (or some other Linux) to connect to the remote Unix server.

You need to connect with the command
```
sftp your_user_name@server.name.whatever
```

sftp is ssh for file transfer. I usually get two terminals, one for ssh and one for sftp. Sftp has fewer features, but you can use "cd" and "ls" like regular bash. In order to get files, you need to use the "get" command. In order to put files on the server, you need to use the "put" command.

Example: suppose that I have my machine and I have /home/me/MyCode folder with a c++ program that will run and create an output file. I write the program on my computer and then I want to go to another more powerful machine and run the program there. Suppose that when I login remotely I am in the folder /users/me.

I would open two terminals. On terminal one I would first go into the folder with my program and then I would sftp:
```
cd /home/me/MyProgram
sftp me@remote.server
cd /users/me/MyProgram
**put my_program.cpp**
```
This assumes that /users/me/MyProgram already exists (use mkdir to create a folder). If your program consists of many files, you can use "put *" or "put *.cpp" to upload all files or the files ending with .cpp.

Then I would go to the second terminal and use regular ssh:
```
ssh me@remote.server
cd /users/me/MyProgram
gcc my_program.cpp (or make)
```
Assuming my program executes and I get back the output file, then I can go back to terminal 1 and issue the "get" command.
```
get output
```

The result is that I now have the "output" file in my /home/me/MyProgram folder.

I hope this is clear enough. Here is some more info on sftp and you can use Google to get more:

[http://www.cae.wisc.edu/linux-sftp](http://www.cae.wisc.edu/linux-sftp)

---

### Post by 3Miro on 2011-08-21
> **Habitual said:**
> rsync is my suggestion.

[http://www.thegeekstuff.com/2010/09/rsync-command-examples/](http://www.thegeekstuff.com/2010/09/rsync-command-examples/)

"Example 4. Synchronize Files From Local to Remote"

Yes, rsync is another solution. The diference is that rsync will create an image of an existing folder and **all** of its files on your hard drive, while sftp will let you select individual files.

---

### Post by Habitual on 2011-08-21
True dat.

But you can also rsync a single file, or a limited number of files singularly. :)

HTH.

---

### Post by 3Miro on 2011-08-21
> **Habitual said:**
> True dat.

But you can also rsync a single file, or a limited number of files singularly. :)

HTH.

Well, rsync does use sftp. If you call an rsync command to a remote server, it will just call a respective sftp command.

If you want to just get one file, use sftp. If you want to keep two folders (or files) "synced" (i.e. all content the same at all times) and do that with minimum traffic, then use rsync.

That's probably the most accurate statement.

---

### Post by MutantJohn on 2011-08-22
Well, thank you all very, very much. You guys were right about the rsync. It worked rather well and now I'm ready to start making galaxies and watch as they hurl themselves towards each other. I'm very happy this place is so helpful, makes me glad I ditched Windows forever.

---

