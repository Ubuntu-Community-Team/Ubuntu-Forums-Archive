---
title: "File names and html"
date: 2012-02-06
forum: General Help
---

### Post by antmenj on 2012-02-06
Hi all

I have a CD that has HTML on it.  Who ever made it has used names such as Welcome.htm in their html wile the corresponding file is called welcome.htm (without the capital "W").

The disc works fine when inserted in a CD drive in ubuntu but once copied to a folder it gets upset over file name differences.  It also works fine from a folder under windowS.

Is there some attribute or similar I can apply to the folder on the hdd to make it non case sensitive or some other fix I can apply?

I am running lucid with firefox 10 but this still happened under hardy back then so I suspect this is more about linux file names than the browser its self.

---

### Post by ajgreeny on 2012-02-06
Presumably all you can do, after backing up the original .htm file, just to make sure you still have it, is to open the code with a text editor or similar and use "find and replace" to see if changing all the letter cases that might be incorrect to the appropriate case is any help.

I presume this problem is due to windows being case independent, therefore welcome = WeLcOmE, etc etc.

---

### Post by Khayyam on 2012-02-06
antmenj ...

hmmm .. I don't think this is due to case sensitivity (it works from the CD after all) I imagine its how it links to files. I would probably convert it using 'wget' .. something like the following should work ..

```
% mkdir mswebything
% cd mswebything
% wget --convert-links file:///path/to/CD/mswebthingy
```This will convert any links in the files and so browsing should work as it does from the CD.

HTH ...

---

### Post by grahammechanical on 2012-02-06
What do you mean: "Gets upset?" That expression does not help us to understand what is happening.

It could be that by copying the contents of the CD you are changing the paths to the documents so that the links do not work.

There is another possibility. Windows uses the back slash ( \ ) in the paths to files. The standard is the forward slash ( / ). The Windows web browser is not fussy, so it will recognise paths that have either the back slash or the forward slash. But a Web browser such as used in Linux and complying strictly to web standards would not recognise a path with the back slash in it.

I know this to be true because HTML documents that I created in Windows complying with the Microsoft way of listing a path to a file, did not work when I switched over to Ubuntu. I had to convert to the industry standard of writing a path.

Regards.

---

### Post by Damascushead on 2012-02-06
I would just edit the html file to reference the correct file.
 
```
sudo gedit Welcom.htm
```
 
or whatever the file name is, and just change any reference to the file to the correct name. 
 
Hopefully the file isn't too terribly big.
 
Hope that helps:p

---

### Post by aasdfasdfg on 2012-02-06
Have you tried opening any of the files from a directory on your computer instead of from a directory in the cd? The filesystem used for cds has various filename restrictions.

---

### Post by antmenj on 2012-02-06
> **grahammechanical said:**
> What do you mean: "Gets upset?" That expression does not help us to understand what is happening.

It could be that by copying the contents of the CD you are changing the paths to the documents so that the links do not work.........

I mean it has broken links.  It contains frames and the frames are empty with can not find file "path/Name" written in it.  File "path/name" is there. (note capitalisation)

I have found a work around.  I copied it to a fat16 USB flash drive and it works fine from that given fat16 is not case sensitive.

Editing each and every html reference is the right thing to do but as there is ~ 150mb of it I can't see that happening any time soon without some type of script etc to clean it all up.

---

### Post by Khayyam on 2012-02-07
> **antmenj said:**
> Editing each and every html reference is the right thing to do but as there is ~ 150mb of it I can't see that happening any time soon without some type of script etc to clean it all up.

antmenj ..

Did you try using wget as I suggested above? This will re-write all links, and **should** resolve the issue.

HTH ..

---

