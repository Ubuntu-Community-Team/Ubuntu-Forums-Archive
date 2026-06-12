---
title: "Folder with 150000 files..most unreadable"
date: 2011-09-19
forum: General Help
---

### Post by mr.najib on 2011-09-19
Hi ALL, 

I would like to solve the following problem.: 
I have extracted 150000 JPEG files from an Iphone, what I want is to pick up those JPEGs which are readable how can I extract them and save them in a different folder?? Most of the JPEGs are not readable ... 

(I have used foremost)

Please help.

Thank you so much in advance!!

---

### Post by hakermania on 2011-09-19
Hello mr.najib, welcome to the forums :)

I have something on my mind as to how to extract the readable JPEG files, but first of all I need you to provide me (attach for example here) with a couple of readable and unreadable images you have, if possible.

---

### Post by cipherboy_loc on 2011-09-19
hakermania:
If he means unreadable aka malformed JPEG headers, you should be able to create a script which finds all the images with a proper header and copy them else where. Also, if they do have malformed headers, it seems like his copy off the iPhone had some issues. 


Cipherboy

---

### Post by hakermania on 2011-09-19
> **cipherboy_loc said:**
> hakermania:
If he means unreadable aka malformed JPEG headers, you should be able to create a script which finds all the images with a proper header and copy them else where. Also, if they do have malformed headers, it seems like his copy off the iPhone had some issues. 


Cipherboy

Hello Cipherboy, I know, that's why I asked to be given a couple of them, I want to search the header of them with the command 'file -b' by looping between them and extracting the real JPEG images.
But I want to see some corrupted, or unreadable ones, because they may have the right JPEG header but they can also be corrupted "from the inside", so I need to see what kind of corruption it is...

---

### Post by mr.najib on 2011-09-20
Thank you all for your contributions!!
I have figured out that the image I have, produced (using foremost) only unreadable jpg files. So should I use another method? Or is there a way of rebuild these corrupt files in a way so that they are readable again?  

So all the files are not readable, how can I post the header of a jpeg file? I guess that foremost checks the header and produce according to the defined header? 
 I am really lost  :sad:

---

### Post by hakermania on 2011-09-20
> **mr.najib said:**
> Thank you all for your contributions!!
I have figured out that the image I have, produced (using foremost) only unreadable jpg files. So should I use another method? Or is there a way of rebuild these corrupt files in a way so that they are readable again?  

So all the files are not readable, how can I post the header of a jpeg file? I guess that foremost checks the header and produce according to the defined header? 
 I am really lost  :sad:

Hey, just provide us with 2 corrupted and 2 normal JPEGs if possible to have a look:guitar:

---

### Post by patryk77 on 2011-09-20
Here is an idea to try:

```
mkdir ~/recovered
for i in $(ls | grep -i jpg); do file $i | grep JPEG >/dev/null; j=$?; if [ $j -eq 0 ]; then cp $i ~/recovered; fi; done

```

What this does is it runs the file command on each image, if file says it contains the JPEG string, it copies it to ~/recovered.

Running:
ls ~/recovered | wc -l
will tell you how many images it copied... Hopefully it won't copy corrupt files, but I make no guarantee ;)

Edit: It is very possible that foremost is using the same method to find possible images (using the [Magic Number](http://en.wikipedia.org/wiki/Magic_number_%28programming%29)) and this might copy all the files...

Edit 2: Sorry hakermania... Now that I took the time to read the whole thread, I see I stole your idea :P

---

### Post by mr.najib on 2011-09-21
Hey folks, 

well thanks again for you help, but as I have posted earlier.. formost produced from the image ONLY corrupted files, so I guess I need to redo the foremost step again? agree, the question is how? I have tried also photorec, nothing works really. Which format is the  iphone saving the pictures? I thought its jpg, I am wrong? 
Regarding the undelete procedure: Do you think I need to take care about the special filesystem my Iphone is using? I dont really know what they use... 

Cheers!!!!

---

### Post by mr.najib on 2011-09-22
any ideas ??

---

### Post by dcstar on 2011-09-22
> **mr.najib said:**
> any ideas ??

The "convert" feature of the **imagemagick** package may be able to be used in a script as it may not create any output for the corrupted files.

---

### Post by hakermania on 2011-09-24
> **patryk77 said:**
> 
Edit 2: Sorry hakermania... Now that I took the time to read the whole thread, I see I stole your idea :P
No worries :)

I'm just curious to see if this solved the problem or not :)

---

### Post by sisco311 on 2011-09-24
> **patryk77 said:**
> Here is an idea to try:

```
mkdir ~/recovered
for i in $(ls | grep -i jpg); do file $i | grep JPEG >/dev/null; j=$?; if [ $j -eq 0 ]; then cp $i ~/recovered; fi; done

```

What this does is it runs the file command on each image, if file says it contains the JPEG string, it copies it to ~/recovered.

Running:
ls ~/recovered | wc -l
will tell you how many images it copied... Hopefully it won't copy corrupt files, but I make no guarantee ;)

Edit: It is very possible that foremost is using the same method to find possible images (using the [Magic Number](http://en.wikipedia.org/wiki/Magic_number_%28programming%29)) and this might copy all the files...

Edit 2: Sorry hakermania... Now that I took the time to read the whole thread, I see I stole your idea :P

That script needs some improvements. :)

```
shopt -s nullglob nocaseglob
for file in ./*.jpg
do
    mime=$(file -b --mime-type "$file")
    if [[ "$mime" == "image/jpeg" ]]
    then
        cp -b "$file" ~/recovered 
    fi
done
```

Please check out BashPitfalls #1 (link in my sig), [http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs), BashFAQ #4 and #20 and [http://bash-hackers.org/wiki/doku.php/syntax/ccmd/if_clause](http://bash-hackers.org/wiki/doku.php/syntax/ccmd/if_clause)

---

### Post by patryk77 on 2011-09-24
> **sisco311 said:**
> That script needs some improvements. :)

Please check out BashPitfalls #1 (link in my sig), [http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs), BashFAQ #4 and #20 and [http://bash-hackers.org/wiki/doku.php/syntax/ccmd/if_clause](http://bash-hackers.org/wiki/doku.php/syntax/ccmd/if_clause)

The irony is, I did read the Bash Pitfalls page after posting this snippet... In another thread someone mentioned you would call them a Hobgoblin were they to use "for i in $(ls)".

Thanks for the links.

On a side note, the reason I was used to using 'in $(ls)' was that if you pass a wildcard as an argument it often complains that the argument list is too long (i.e.: mv /tmp/motion/*.jpg /other/path), when there are too many files matching.

I take it Bash doesn't have that problem, since it's an array and not arguments?

---

### Post by mr.najib on 2011-09-24
So well I have tried out the methods mentioned, I could at least copy some big files about 12MB .... however the problem is that even these good files are not readable. It makes not sense when all of them are not readable :p

So the whole foremost procedure is not working. How can I find a solution for this.
When I created the image from the iphone there was not any failures... I suppose that the image is ok. 
I should get at least the pictures I still have on my phone, right?  do not know why this is not working...

---

### Post by David Andersson on 2011-09-24
First I want to clarify, do you mean by "unreadable" that the file content is not jpeg or corrupted? Or do you mean that you as a user do not have read permissions to the files? (The later is a possibility if you ran foremost as root, i.e. sudo foremost.)

In the package *recoverjpeg* there is a tool *remove-duplicate*. It is likely that multiple copies have been recovered for some of the images, and it is a pain to try and find them manually.

In the same package there is also a tool *sort-pictures* that organize images by date, provided the images had exif headers.

---

### Post by mr.najib on 2011-09-24
well I mean that the files have the jpeg format but when I open one its says :
Could not load image.... Error interpreting JPEG image file (unsopported marker type 0 x9a)

---

### Post by hakermania on 2011-10-01
> **mr.najib said:**
> well I mean that the files have the jpeg format but when I open one its says :
Could not load image.... Error interpreting JPEG image file (unsopported marker type 0 x9a)
Ok, so it detects that it's a JPEG, so the header is here..... Hmmm, hmmmm, hmmmm, please tell me, do the corrupted JPEG files have anything other special that make them differ from the normal JPEGS?

---

### Post by hakermania on 2011-10-05
Anyway, if anyone ever follow this thread, you could use 'identify' from the imagemagick package and check the return code via the $? variable each time. Do the corresponding action with the corresponding exit code...

---

