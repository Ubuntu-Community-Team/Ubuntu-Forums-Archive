---
title: "Help with CeltX"
date: 2011-06-05
forum: General Help
---

### Post by MidniteMagus on 2011-06-05
Hello all,

I'm a brand new Linux user and though in the past I was somewhat familiar with command prompts, all the years of having Windows hold my hand has left me rather rusty. Luckily, up till this point I've found that most software can be installed to Ubuntu rather easily. However, I've been trying to install CeltX and I've ran into a problem.

I downloaded the file Celtx-2.9.1.tar.bz2 from the Celtx website, and as I've been getting familiar with these packages I went to open the file using the usual commands but I kept getting an error. Then I tried Google for instructions. I found the CeltxWiki which told me to use the following commands:

sudo tar xjf /path/to/Celtx.tar.bz2 
(enter your password) 
sudo /usr/local/celtx/celtx


[FONT=monospace][/FONT]For some reason I had a blonde moment and assumed that '/path/to' meant that I was supposed to enter the location of the file. Now I have a folder in my Home folder that I can't get rid of called CeltX, but it doesn't do anything and I still don't have the program installed. When I try and follow the instructions it tells me that there is no such file or directory and now I'm totally lost. 

I know that you guys must get people like me begging for help all the time, but I really don't to clutter up my brand new installation just because I'm Linux stupid. Any help you guys can offer would be greatly appreciated.

---

### Post by timgood on 2011-06-05
You were not so blonde after all. You have unpacked the celtx directory to your home folder. Inside that folder should be the celtx executable which you can run from terminal. For example, my home directory is called 'tim' so from terminal I would write:

```
/home/tim/celtx/celtx &
```which launches the program. You can also make a new launcher for your panel (if using Ubuntu 10.x) or the sidebar if you are using Unity. The executable in the celtx directory is called celtx. The reason you can't get rid of the folder is because you unpacked it as 'root' (using sudo) so the files aren't owned by you. To fix this: ```
 sudo chown insertyourusernamehere -R /home/yourusername/celtx 
```

Hope this helps.

---

### Post by MidniteMagus on 2011-06-05
Thanks! That enabled me to remove it from my Home folder, but I still can't figure out how to put it in the right place. I guess I'm used to Windows where when a program is installed it goes into a Program Files area and isn't right in there with your other documents. Is that how Linux should work too? Or is the Home folder where it should be?

---

### Post by MidniteMagus on 2011-06-05
Never mind, I have since figured things out and danced a little victory dance. I feel like my brain is waking up from a Window's induced fog. I could really get used to this Linux thing... 

Thanks for all your help!

---

### Post by timgood on 2011-06-05
> **MidniteMagus said:**
> Thanks! That enabled me to remove it from my Home folder, but I still can't figure out how to put it in the right place. I guess I'm used to Windows where when a program is installed it goes into a Program Files area and isn't right in there with your other documents. Is that how Linux should work too? Or is the Home folder where it should be?

Because Celtx is not packaged in .deb format, you can install it pretty much where you want. All the dependencies are included in the folder celtx, along with the binaries to launch it. Many purists would want to unpack the celtx folder to the /opt directory, and run it from there. I simply put the folder celtx in my home directory and run it from there. As I use Cairo Dock I have created a launcher which runs the program from the dock. 

With Linux, there is not necessarily a 'right place' to install to. Most .deb packages will install binaries to /usr/bin or /bin because the installation is 'system wide' and runs with root (sudo) privileges. But because Linux is more secure than Windows, permissions can enable different users to have independent software installations in their home directories, or in other directories to which they have the relevant read or write permissions.

If you simply want Celtx to work for 1 user (yourself), right click on the downloaded tar.bz2 package and select 'Extract Here'. Then move the folder 'celtx' to your home directory, or any other directory in which you have read/write permissions, and create a launcher to launch the application. The executable is in the celtx folder and is called celtx. If you would like Celtx to be 'system wide' (used by more than 1 user) then extract it as before and then move it to the /opt directory, and run it from there.

Hope this helps.

---

### Post by byrdiblack on 2013-03-31
> **timgood said:**
> Because Celtx is not packaged in .deb format, you can install it pretty much where you want. All the dependencies are included in the folder celtx, along with the binaries to launch it. Many purists would want to unpack the celtx folder to the /opt directory, and run it from there. I simply put the folder celtx in my home directory and run it from there. As I use Cairo Dock I have created a launcher which runs the program from the dock. 

Thank you so much for your help with launching Celtx! I, too, am a total noob but followed your instructions to move to the home folder and was able to launch it from the terminal.
I was wondering if you could provide more detailed instructions on creating a launcher so that I can have open from the dock?

I'm currently using Ubuntu 12.10 and when I right click Celtx as its running and lock it to the dock, it just becomes a floating icon with no click response after the program closes. I'd love to learn about creating a launcher that will work! Thanks in advance!

---

### Post by wildmanne39 on 2013-03-31
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

