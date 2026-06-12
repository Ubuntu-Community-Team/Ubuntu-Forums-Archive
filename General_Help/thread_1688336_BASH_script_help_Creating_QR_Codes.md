---
title: "BASH script help? Creating QR Codes"
date: 2011-02-15
forum: General Help
---

### Post by tom.swartz07 on 2011-02-15
Hi all, 

I'm trying to create a BASH script that will read a .txt file that contains URLS to various websites, parse it, and create QR codes for each line. 

So far, the simple script looks like this:
```
while read line
do
	echo -e "$line"
        qrencode -l L -o "$line".png $line
done < urls.txt
```

I keep getting the error ```
Failed to create file: ieeexplore.ieee.org/mobile/.png
No such file or directory
```
You could substitute ieeexplore.ieee.org/mobile/.png for any of the urls that I am trying to encode. It won't encode any of them.

Could anyone help debug this program for me? Im totally lost.....

---

### Post by gmargo on 2011-02-15
This is very difficult without an example of your input file.

Does the output directory already exist?

---

### Post by hawkmage on 2011-02-15
I am not familiar with the command options of qrencode but it looks like you are trying to create a file named ".png" in a directory named "mobile" under a directory named "ieeexplore.ieee.org" under the current directory.  

Is there a directory named "ieeexplore.ieee.org" exist? and does the "mobile" directory exist under it for the application to create the file named ".png" in it?

If you are using bash as the shell you can try this instead:
```
qrencode -l L -o "${line//\//_}".png $line
```
This will replace the "/" with "_".

---

### Post by tom.swartz07 on 2011-02-15
> **gmargo said:**
> This is very difficult without an example of your input file.

Does the output directory already exist?

My example input file looks like this:
```
market.android.com/details?id=com.bim.pubmed
www.apple.com/webapps/utilities/mobilepubmed.html
ieeexplore.ieee.org/mobile/
```
Just plain text, one URL per line.

It should encode the url and output 1 QR code per line on the local machine directory

---

### Post by gmargo on 2011-02-15
Does your input file have CR-LF line endings?  If so, you have to strip the bonus carriage return.  Try adding this to your script to clean up the input:
```

        line=$(echo "$line" | sed 's/\r//')

```

---

### Post by hawkmage on 2011-02-15
OK if you are gong to have more special characters than just "/" in the string you will need a more complex replacement statement.

Allong the lines of:
```
qrencode -l L -o "${line//[\/?]/_}".png $line
```
This will replace any characters that you put between the [ and ] with a "_"

---

### Post by gmargo on 2011-02-15
> **tom.swartz07 said:**
> output 1 QR code per line on the local machine directory

So you are expecting the local machine to end up with these files:
```

market.android.com/details?id=com.bim.pubmed.png
www.apple.com/webapps/utilities/mobilepubmed.html.png
ieeexplore.ieee.org/mobile/.png

```Who is creating the directory structure for these output files on the local machine?

---

### Post by hawkmage on 2011-02-15
> **gmargo said:**
> Who is creating the directory structure for these output files on the local machine?
That is the issue, nothingnis creating the directories for the files to be written into.  That is why I recomended to change the line info so that the application will not treat them as directories

---

### Post by wormyblackburny on 2011-02-15
+1 Hawk

From the qrencode command, the ouput file you are telling it to create has / which the shell is going to interpret as directory structure. You need 2 variables for example:

$line (which is the literal URL you are encoding, obviously this needs to remain intact
$name (this is the name of the outputted .png image

Get the line and convert all specials (and ///) to say periods or underscores and assign it to $name then do

qrencode -l L -o "$name".png $line

If the URL's are simple and do not go too deep into the directory tree (like foobar.com/index.html) just change the / to colons and cut the first part of the url and drop everything after the first /. I guess it all depends on how specific you want the filenames to be for the image vs. the actual URL of the site you are converting.....

---

### Post by tom.swartz07 on 2011-02-15
> **wormyblackburny said:**
> +1 Hawk

From the qrencode command, the ouput file you are telling it to create has / which the shell is going to interpret as directory structure. You need 2 variables for example:

$line (which is the literal URL you are encoding, obviously this needs to remain intact
$name (this is the name of the outputted .png image

Get the line and convert all specials (and ///) to say periods or underscores and assign it to $name then do

qrencode -l L -o "$name".png $line

If the URL's are simple and do not go too deep into the directory tree (like foobar.com/index.html) just change the / to colons and cut the first part of the url and drop everything after the first /. I guess it all depends on how specific you want the filenames to be for the image vs. the actual URL of the site you are converting.....


Yep, this is just what I needed! Thanks Hawk and Wormy. It turns out that it WAS in fact looking for the directory structure, instead of the ONLINE url that I was hoping for. Once I changed the name of the file to replace the forward slash symbols, It works great!

Thanks so much for the help!

---

