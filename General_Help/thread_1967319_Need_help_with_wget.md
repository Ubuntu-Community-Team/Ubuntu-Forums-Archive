---
title: "Need help with wget"
date: 2012-04-28
forum: General Help
---

### Post by christopher.suttles on 2012-04-28
Hello all. I am new here. I recently kicked my windows addiction. Ubuntu 12.04 is my only OS. I have been putting the move off for about a year now. ):P

Anyways, I need some help pulling some pictures from a website using wget.

They consist of .jpg, .png, and .gif files.

The main problem is they are spread across multiple pages, with only 1 picture per page. There are a total of 2,691 pictures i want.

They are spread across pages in this format:

[http://www.example.com/image/1](http://www.example.com/image/1)
all the way to
[http://www.example.com/image/2691](http://www.example.com/image/2691)

Please not the extensions for these pictures are spread out randomly across. So basically I am wondering what the command would be to download from each one of those pages only looking for the extensions listed above.

---

### Post by ahso4271 on 2012-04-28
man wget

---

### Post by prshah on 2012-04-28
> **christopher.suttles said:**
> 
Anyways, I need some help pulling some pictures from a website using wget.

They consist of .jpg, .png, and .gif files.


Typically, you should use```
$  wget -r -l4 --no-parent -A jpg,png,gif http://www.example.com/image/
``` where:

-r = recursive
-l4 = retrieve files upto four subdirectories deep (increase as you feel required)
--no-parent = do not travel "up" the directory structure
-A = comma seperated list of acceptable files

---

### Post by christopher.suttles on 2012-04-28
> **prshah said:**
> Typically, you should use```
$  wget -r -l4 --no-parent -A jpg,png,gif http://www.example.com/image/
``` where:

-r = recursive
-l4 = retrieve files upto four subdirectories deep (increase as you feel required)
--no-parent = do not travel "up" the directory structure
-A = comma seperated list of acceptable files

Thanks for the quick replies. Using "man wget" I was able to almost figure it out myself. This is what I have been using..

  	 	 	 	 	 	   wget -nd -r -l1 -P /home/christopher/Downloads/Bleh -A jpeg,jpg,bmp,gif,png [http://www.example.com/image/1](http://www.example.com/image/1)


That puts the image i need into the folder. But I dont want to have to do it some 2600 hundred times.


So is there any way I can tell it to download that from each different url? I used some batch programs in windows before. I tried using it like this


wget -nd -r -l1 -P /home/christopher/Downloads/Bleh -A jpeg,jpg,bmp,gif,png [http://www.example.com/image/](http://www.example.com/image/)[1:2691]


Which would tell it to download each url differently. Anyway to do that via wget, or am I going to have to create a .txt file with each url and load that? (and if thats how I have to do it, any way to generate the lines of text automatically?)

---

### Post by prshah on 2012-04-28
> **christopher.suttles said:**
> wget -nd -r -l1 -P /home/christopher/Downloads/Bleh -A jpeg,jpg,bmp,gif,png [http://www.example.com/image/1](http://www.example.com/image/1)


Don't give the filename in the url; just give the base directory (eg, [www.example.com/image](www.example.com/image)).

Normally this will download ALL files; however the accept list (-A) will only actually download the files that are matched.

You don't need the "-nd" because the images will be downloaded with directory structure. You can then use the "find" command to move all image files into a single directory (if you so require).

You will also have to increase the recursive depth (-l1), typically to 2 or three, to ensure that subdirectories under your target are captured properly.

You must also use the "--no-parent" switch, to prevent "upward" movement through directories.

Hope this is clear.

---

### Post by christopher.suttles on 2012-04-28
Aha!

Thanks prsha, I have it now. Appreciate the help!

---

