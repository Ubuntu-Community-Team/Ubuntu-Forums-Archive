---
title: "How to make certain files/folders invisible to specific users?"
date: 2011-01-07
forum: General Help
---

### Post by HimeNoHogosha on 2011-01-07
I've got a NAS running and I'd like to somehow make some of the folders and files invisible to certain users only. For example, if I 'ls' a directory, I want to see files 'a', 'b', and 'c'. But if another user does 'ls' in the same directory, I only want them to be able to see 'a' listed.

I know I can use 'chmod +700' to make certain files not able to be read/written, but the filename would still appear in a 'ls'. 

I know I can put certain files inside of a '.hidden' file in the folder, but then it would be hidden from myself as well.

Is what I'm trying to do possible?

Edit : I'd also like to mention that the users that connect to the NAS could be coming from Windows or Mac operating systems. So hopefully the solution would work for users from those systems also..

---

### Post by anglican on 2011-01-07
> **HimeNoHogosha said:**
> I've got a NAS running and I'd like to somehow make some of the folders and files invisible to certain users only. For example, if I 'ls' a directory, I want to see files 'a', 'b', and 'c'. But if another user does 'ls' in the same directory, I only want them to be able to see 'a' listed.

I know I can use 'chmod +700' to make certain files not able to be read/written, but the filename would still appear in a 'ls'. 

I know I can put certain files inside of a '.hidden' file in the folder, but then it would be hidden from myself as well.

Is what I'm trying to do possible?

Edit : I'd also like to mention that the users that connect to the NAS could be coming from Windows or Mac operating systems. So hopefully the solution would work for users from those systems also..I don't know of any direct way to do this with ls. A possible workaround might be to use the colors that ls produces for different file types to render them invisible. See the man pages for "dircolor" and "dir_colors" for how to do this. Basically you can add to the defaults, for example to make files with extension .xyz invisible you would add ```
*.xyz=37;47
```to the LS_COLORS shell variable and then ls would show a blank white/grey block for those files. A bit lame I'm afraid, but the "." at the beginning of the name is the Unix/Linux way to hide things normally. So if you add the export "LS_COLORS=..." to the users .bashrc you can make some files invisible(ish) to ls.

H

---

### Post by dino99 on 2011-01-07
To hide a file or folder in Nautilus, either rename the file so its name begins with the period (.) character, or create a text file named .hidden in the same folder, and add its name to it, as in the example below:

filename
foldername


[http://chetangole.com/blog/2008/11/how-to-hide-or-protect-folders-in-ubuntu-linux/](http://chetangole.com/blog/2008/11/how-to-hide-or-protect-folders-in-ubuntu-linux/)

---

### Post by HimeNoHogosha on 2011-01-07
Well I wouldn't want to add a '.' in front of all the files because they would then have a different filename, and also I don't want the files to be hidden to everybody. I also don't want to just play with the colors because that wouldn't work for people using Windows or Mac.

The '.hidden' thing kind of works, but the problem is the user can still see the folder, and it's when they try to access it they are notified that they don't have permissions. But I'm trying to go one step before that and make the folder not even visible to them in the first place so they don't know it's there at all.

I kind of wish that in addition to read/write/execute permissions, there was visibility permission...

---

### Post by dandnsmith on 2011-01-07
Correct me if I have the wrong impression, but the NAS is the key element here, as that is where the permissions will reside, under the control of whatever OS drives the NAS.

It's a good chance that it will be a customised linux - but where do you go from there? The rules on your own PC won't be applied on the NAS.

---

### Post by pastalavista on 2011-01-07
You might try [Gobohide]("http://www.webupd8.org/2011/01/how-to-really-hide-folders-in-ubuntu.html"), which will actually make folders invisible to everyone and can only be opened if you know the exact path/to/secret/folder-name... that only you will know.. so don't forget it.

---

