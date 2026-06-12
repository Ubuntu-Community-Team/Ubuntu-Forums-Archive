---
title: "Cant insert image in web page"
date: 2011-12-09
forum: General Help
---

### Post by &lt;/o=Dog&gt; on 2011-12-09
I am building a simple web site and i wont to insert an image background, i am using nano to edit the index.html and so far so good, its exactly what i want, but when i wright the code for inserting animage background  the image dosn't show up on my web page, so i edited another file and saved it as "index.html.save"in the same directory as the default index.html and typed the path into my search bar "File:///var/www/index.html.save" and it worked perfectly the permissions are exactly the same and i know my coding is correct, i am using apache2 and the default index.html for my web page, is there a setting in apache to accomplish this as i am sure there must be somthing that i have missed please help as im going out of my mind trying to figure this out. thanx

---

### Post by WorMzy on 2011-12-09
You mean the image displays locally, but not when the page is accessed via apache? Could be a permissions problem; if apache can't read the image, then it can't serve it to you.

Does apache's access and error logs give any hints as to what's going wrong?

---

### Post by lisati on 2011-12-09
Does the image show up when you clear your browser's cache and reload the page?

---

### Post by &lt;/o=Dog&gt; on 2011-12-09
yes when veiwed locally everything is fine when veiwed through my web site url the background and images don't show up, i was told that the images folder had to be in the same directory as the index.html file but when i do that i cant access the folder to write to it, the images are stored locally on drive and i have pointed to them in my coding, i think you are probably right about the permission bit though is there way i can adjust this

---

### Post by &lt;/o=Dog&gt; on 2011-12-09
one of the first things i tried, no cigar

---

### Post by WorMzy on 2011-12-09
How are you pointing at them? The addresses have to be either relative to the webserver's root folder, or relative to the page's location (but you must remain within the webserver's root folder).

e.g. if the image is in /var/www/images/image.png, then the address in the css to set the background image would be "/images/image.png", or "images/image.png" (assuming the page is /var/www/index.html)

So you can't, for instance, use /home/dog/Pictures/image.png, because the webserver doesn't know about that folder.

---

### Post by &lt;/o=Dog&gt; on 2011-12-09
i;ve looked on the logs in apache and there is nothing in there that tells me anything about the images not being served

---

### Post by &lt;/o=Dog&gt; on 2011-12-09
right i think that is what i am doing wrong, but how do you get a folder images in the var/www directory and put an image there as it want let access to create directory in there? As root in the terminal i manages to create a folder for the images to go but dosent allow images to be copied to that folder at all

---

### Post by lisati on 2011-12-09
> **</o=Dog> said:**
> right i think that is what i am doing wrong, but how do you get a folder images in the var/www directory and put an image there as it want let access to create directory in there? As root in the terminal i manages to create a folder for the images to go but dosent allow images to be copied to that folder at all

What I usually do is put the file or folder in a place I can access e.g. using samba or ftp, then use something like **sudo cp *{details}*** to get it to the proper place in /var/www. For example, if I have a folder **temp** in my home folder on the server, and I want it copied in its entirety to /var/www, I'd use ```
sudo cp -r ~/temp /var/www/
```

---

### Post by WorMzy on 2011-12-09
There's differing schools of thought about that. You can either:

A) change the permissions on the webserver's folder to allow everyone to write to it (this is considered very insecure and a Very Bad Idea&#8482;)

B) change the ownership of the folder, from root to your user, or change the group ownership of the folder to a group that you belong to, then make sure that the group has write access to the folder. (this is somewhat insecure, but it means that someone would have to log in as you to edit anything)

C) use a file manager, run with gksudo (so as root), to transfer files across (this is considered the most secure, but remember to close the file browser after you're done). You could, instead of using the file browser, move things using the command line, with sudo; but be careful not to make a mistake.

---

### Post by &lt;/o=Dog&gt; on 2011-12-09
i have established that i am not pointing to a directory in the right place, i have used the code for copying a folder with my .gifs for my background and images into the var/www/ directory i have edited the code to point to that directiory and still no joy will not load them at all, still will locally. i dont really want to ajust the permissions for security reasons so is they any setting within the apsche server itself to enable these images to be shown.

---

### Post by WorMzy on 2011-12-09
I doubt that they're disabled in apache's config, unless you've specifically made it so that they are. ;)

Make sure that the copied files and folders have read access for "others", and that the addresses in the code are correct. If you're not sure, post the code here, along with a directory listing (ls -lR /var/www), and I'll take a look at it.

Post code and terminal output between [code[COLOR="Black"]][[/COLOR]/code] tags, please.

---

### Post by &lt;/o=Dog&gt; on 2011-12-09
code as it appears in the index.html :-
<body background="/var/www/www.images/ball.gif">

root@dog-server:/var/www# dir
Graphics  index.html  index.html.save  index.html.save.1  [www.images](www.images)
root@dog-server:/var/www#

---

### Post by WorMzy on 2011-12-09
Oh blimey, I haven't seen someone use dir in years. Try the ls command I posted. I need to be able to see the permissions of the files in question (e.g. -rwxr-xr-x)

And you're still not using a path relative to the server's root folder. Change "/var/www/www.images/ball.gif" to "/www.images/ball.gif".

I won't comment on you using html rather than css to control presentation. I just hope you're not planning on making an actual website like that. ;)

---

### Post by lisati on 2011-12-09
> **WorMzy said:**
> Oh blimey, I haven't seen someone use dir in years. Try the ls command I posted. I need to be able to see the permissions of the files in question (e.g. -rwxr-xr-x)

:D I sometimes use "dir", and the ls command you mentioned:
```
ls -al
```

---

### Post by &lt;/o=Dog&gt; on 2011-12-09
Apologies for  the dir command thing, but i am old school back in the days of  DOS batch files and such LOL, about the html thing i am writting and learning as i go along with html and the web page is just a simple effort want of a better word. just to see if i could, i was once told  in computing "to go forward first go backwards" and after seeing linux in all its glory its just another play thing to get my head around any way back to the point........

-rw-r--r-- 1 root root 2071 2011-12-09 22:20 index.html
-rw-r--r-- 1 root root 2072 2011-12-09 13:49 index.html.save
-rw-r--r-- 1 root root 2071 2011-12-09 22:49 index.html.save.1

---

### Post by WorMzy on 2011-12-09
Unless you've had a bit of a tidy, you must have missed some of the output.

ls = list files
-l = in long format (with permissions)
-R = recursive listing (shows contents of folders)

lisati suggested using the -a flag, which shows all "hidden" files as well. I don't think that would be useful in this situation, but you use it as well if you want:

```
ls -alR /var/www
```

Anyway, it may not be necessary. Did you try changing the address like I suggested? Remember that the webserver can only see inside the folders it's been set up to use. By default, that's just /var/www. So you telling the webpage to use /var/www/www.images/ball.gif, makes the webserver look for that *inside* /var/www, so it looks for /var/www/var/www/www.images/ball.gif, which obviously doesn't exist.

---

### Post by &lt;/o=Dog&gt; on 2011-12-09
yes i got rid of the extra folders and created a new one containing the gifs i want to put in my page the whole thing looks like this.....

total 24
drwxr-xr-x  3 root root 4096 2011-12-09 23:29 .
drwxr-xr-x 15 root root 4096 2011-12-04 23:09 ..
drwxr-xr-x  2 root root 4096 2011-12-09 23:29 images
-rw-r--r--  1 root root 2071 2011-12-09 22:20 index.html
-rw-r--r--  1 root root 2072 2011-12-09 13:49 index.html.save
-rw-r--r--  1 root root 2071 2011-12-09 22:49 index.html.save.1

/var/www/images:
total 48
drwxr-xr-x 2 root root  4096 2011-12-09 23:29 .
drwxr-xr-x 3 root root  4096 2011-12-09 23:29 ..
-rw-r--r-- 1 root root 17062 2011-12-09 23:29 ball.gif
-rw-r--r-- 1 root root  3775 2011-12-09 23:29 football.gif
-rw-r--r-- 1 root root 13000 2011-12-09 23:29 Pitch.gif

how do get the files straight to the www directory as that is what i am getting "the folder dosent exist" when trying to copy them.

---

### Post by WorMzy on 2011-12-09
> how do get the files straight to the www directory as that is what i am getting "the folder dosent exist" when trying to copy them. 

Not sure I understand the question. You're trying to get the images into /var/www, rather than /var/www/images, but keep getting a "folder doesn't exist" error? Not sure why that would be. What command are you using?


Before you move anything though, just check whether you can access the images from the webserver. The permissions check out, so you should be able to see the images if you point your browser to, for example, [http://localhost/images/football.gif]("http://localhost/images/football.gif").

---

### Post by &lt;/o=Dog&gt; on 2011-12-09
copying the files straight into the www directory so not using the images folder but i am getting images file dosent exist the command i am using is sudo cp -r ~

When i try to go to the images as you suggested i get this in the page

The requested URL /images/football.gif. was not found on this server.

---

### Post by &lt;/o=Dog&gt; on 2011-12-09
> **WorMzy said:**
> Not sure I understand the question. You're trying to get the images into /var/www, rather than /var/www/images, but keep getting a "folder doesn't exist" error? Not sure why that would be. What command are you using?


Before you move anything though, just check whether you can access the images from the webserver. The permissions check out, so you should be able to see the images if you point your browser to, for example, [http://localhost/images/football.gif](http://localhost/images/football.gif).

I could access the file using my server web address added the web address into my file and BINGO!!!!
it worked, if you hadn't suggested using [http://localhost/images/football.gif](http://localhost/images/football.gif) i would never have got it 

thanx very much for your help its been a real learning curve and i have learned i few more commands to my tally how do you set as solved please thanx:D:D

---

### Post by WorMzy on 2011-12-09
> **</o=Dog> said:**
> The requested URL /images/football.gif. was not found on this server.

Remove the full stop from the url, you weren't meant to include that. :P

> sudo cp -r ~

That's technically an incomplete command, you're missing the final argument, which is the destination for the files. Unfortunately, the ~ is expanding to *everything* in your home folder, so it's not telling you this, what it's trying to do instead, is move everything in your home folder, except for the last file, into the last file, which it can't do, because the file isn't a folder. Be careful with cp commands; I don't think you meant to copy everything in your home folder; I certainly would advise against it.

Stick to copying individual files and folders for now, and remember to always include a destination for the copied files.

---

### Post by WorMzy on 2011-12-09
> **</o=Dog> said:**
> I could access the file using my server web address added the web address into my file and BINGO!!!!
it worked, if you hadn't suggested using [http://localhost/images/football.gif](http://localhost/images/football.gif) i would never have got it 

thanx very much for your help its been a real learning curve and i have learned i few more commands to my tally how do you set as solved please thanx:D:D

How to mark as solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)


The thing about using full paths like that, is that, to an outsider, that address won't work. If your webserver was accessible from outside your network (e.g. if I could access it from my web browser), then I'd get a 404 page not found error for the image, because my [http://localhost](http://localhost) is my webserver, not yours.

If [http://localhost/images/football.gif](http://localhost/images/football.gif) works as the background URL in the html, then "/images/football.gif" should work too.

---

### Post by Paddy Landau on 2011-12-09
> **WorMzy said:**
> Stick to copying individual files and folders for now, and remember to always include a destination for the copied files.
Or, as already stated, use the GUI. Press Alt-F2 and enter:```
gksudo nautilus
```Do only what you need to do and then close the window.

---

