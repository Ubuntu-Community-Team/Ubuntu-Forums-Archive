---
title: "Diff file with the hole folder cotent"
date: 2012-03-06
forum: General Help
---

### Post by JCM_Pico on 2012-03-06
I there is there any way of Diff file with the hole folder cotent

---

### Post by MG&amp;TL on 2012-03-06
If you mean comparing folders:

```
diff -r folder1 folder2
```

---

### Post by JCM_Pico on 2012-03-06
nop.... one file against all the other files within the same folder

---

### Post by Khayyam on 2012-03-06
Something like:

```
for i in files/* ; do
    diff file ${i} > ${i}.txt
done
```best ... khay

---

### Post by JCM_Pico on 2012-03-07
> **Khayyam said:**
> Something like:

```
for i in files/* ; do
    diff file ${i} > ${i}.txt
done
```best ... khay

why ${i}.txt...

---

### Post by Khayyam on 2012-03-07
> **JCM_Pico said:**
> why ${i}.txt...

${i} is the variable of the "for" loop. It could be written:

```
for file in files/* ; do
    diff file ${file} > ${file}.txt
done
```

But that would be ... ummm ... confusing :)

best ... khay

---

### Post by JCM_Pico on 2012-03-07
> **Khayyam said:**
> ${i} is the variable of the "for" loop. It could be written:

```
for file in files/* ; do
    diff file ${file} > ${file}.txt
done
```But that would be ... ummm ... confusing :)

best ... khay

I know that ${i} is the variable... I was wondering why .txt ... if it was there for some reason... because I think this loop will test the file against it self   :confused:

---

### Post by JCM_Pico on 2012-03-07
I was wonder if it could be done something like this

```
for i in find / \( ! -name "file_to_test.txt" \) -type f ; do
    diff file ${i} > file_to_test.txt
done
```

This way I would test file file_to_test.txt against all the other... it would be great 
But I cant find a way to put the find feeding the loop

---

### Post by sudodus on 2012-03-07
> **JCM_Pico said:**
> I know that ${i} is the variable... I was wondering why .txt ... if it was there for some reason... because I think this loop will test the file against it self   :confused:
It is only a text file, that contains the redirected output to the screen. I would have appended the output ( >> instead of > ), and maybe written that file to some place outside the current directory.

---

### Post by JCM_Pico on 2012-03-07
OK I found a way of doing it 

```
find /home/user/folder/*.jpg \( ! -name "file_to_test.txt" \) -type f -exec diff {} "file_to_test.txt" \;
```

Thanks a lot.... your ideas helped me think :p

---

### Post by Khayyam on 2012-03-07
> **JCM_Pico said:**
> I know that ${i} is the variable... I was wondering why .txt ... if it was there for some reason... because I think this loop will test the file against it self

Note there are three items on that line 1). the file, this is, the file you are comparing all the other files to 2). ${file} the files to be compared against, and 3). "> ${file}.txt" where the output of each diff will be redirected to.

It won't be "against itself" as "file" and "files/*" are in different directories.

Test:

```
echo file && for i in files/* ; do echo ${i} ; done
```

best ... khay

---

### Post by JCM_Pico on 2012-03-07
> **Khayyam said:**
> Note there are three items on that line 1). the file, this is, the file you are comparing all the other files to 2). ${file} the files to be compared against, and 3). "> ${file}.txt" where the output of each diff will be redirected to.

It won't be "against itself" as "file" and "files/*" are in different directories.

Test:

```
echo file && for i in files/* ; do echo ${i} ; done
```best ... khay

Hooo... Sorry mate... your are right I misunderstand it 

Thanks

---

### Post by Khayyam on 2012-03-07
> **sudodus said:**
> It is only a text file, that contains the redirected output to the screen. I would have appended the output ( >> instead of > ), and maybe written that file to some place outside the current directory.

Each ${file}.txt will be different, one for each diff ... reading diffs is hard enough without appending them all to the same file. Anyhow, I was just illustrating the method, the madness has to be provided by the user :)

best ... khay

---

### Post by JCM_Pico on 2012-03-07
Here's the script I've made with your help... I use it to download images from an online weathercam every 2 minutes (set as a cronjob) and at the end of the day all the files are converted to a timelapse.....
I faced a problem - sometimes there were problems in the cam and the image would be the same... making the timelapse to show the same image for like 10 minutes... with the IF and using FIND I test the downloaded files against all the other downloaded files and the script removes it if its equal.... :p

```
#!/bin/bash
# Script to download image from an online weathercam
# By JCM_Pico

workdir=/any/folder/

if [ -d ${workdir} ]
then
        echo ${workdiri} directory  exists!
else
        echo ${workdir} directory not found!
        echo creating directory
        mkdir ${workdir}
fi

cd ${workdir}

imgdate=$(date +%Y%m%d%H%M)
urlpath="http://wethercam_location.jpg"

wget --tries=20 --continue ${urlpath} -O ${imgdate}.jpg

if find ${workdir}*.jpg \( ! -name ${imgdate}.jpg \) -type f -exec diff {} ${imgdate}.jpg \;
then
  rm ${imgdate}.jpg
  echo files WERE removed
else
  echo Different - NO files were removed
fi
                       
```

---

### Post by Khayyam on 2012-03-07
BTW, if your comparing jpegs then you should really use something like [PIL](http://www.pythonware.com/products/pil/), Python Image Library, 'diff' will only provide you with string comparison (and thats not what you want).

Or, if  you're looking for a copy comparison, try comparing  the MD5 hash of both files.

best ... khay

---

### Post by JCM_Pico on 2012-03-07
> **Khayyam said:**
> BTW, if your comparing jpegs then you should really use something like [PIL]("http://www.pythonware.com/products/pil/"), Python Image Library, 'diff' will only provide you with string comparison (and thats not what you want).

Or, if  you're looking for a copy comparison, try comparing  the MD5 hash of both files.

best ... khay

I thought diff would make a check sum to the image.... albeit all that.... the script is working fine  for the test that I've made... deleting if the image is the same :)
But I would be amazed if I did it with python... I would like very much to start working with python to use it instead of matlab in must of my work scripts but the lack of time have been stopping me... :(

---

### Post by Khayyam on 2012-03-07
> **JCM_Pico said:**
> I thought diff would make a check sum to the image.... albeit all that.... the script is working fine  for the test that I've made... deleting if the image is the same. But I would be amazed if I did it with python... I would like very much to start working with python to use it instead of matlab in must of my work scripts but the lack of time have been stopping me.

No, your right, diff will do basic comparison on jpegs, and this is probably all you require. I use diff for text comparison, and in that regard its output is often verbose.

PIL is a library with lots of features so it might be a good place to start of your looking for someplace to start with python.

best ... khay

---

### Post by JCM_Pico on 2012-03-07
OK... the find works with the diff but I'm not being able tom implement it in the IF statement... it allways removes the file... :-(

---

### Post by Khayyam on 2012-03-07
> **JCM_Pico said:**
> OK... the find works with the diff but I'm not being able tom implement it in the IF statement... it allways removes the file.

Well, you have an if statement that simply runs the diff ... I don't know what you expect to happen. If statements have to test the truth of something. Its really hard to see what your trying to do as comparing a number of images to one image will always be a question of {n} misses to every hit. Why do you need to compare all the images in this directory?

Anyhow ... I cleaned up you script a little and added a test based on the return value of each diff (2 fail , 0 sucess). Its a little vague as to what its doing but it should give you something clearer to work from (you script above is rife with typos, and errors)

```
#!/bin/bash

WORKDIR=$HOME/Weathercam

if [[ ! -d ${WORKDIR} ]] ; then
    mkdir ${WORKDIR}
fi

IMGDATE=$(date +%Y%m%d%H%M)
URLPATH="http://wethercam_location.jpg"

wget --tries=20 --continue ${URLPATH} -O ${TMPDIR}/${IMGDATE}.jpg

for i in ${WORKDIR}/*.jpg ; do
    diff ${TMPDIR}/${IMGDATE}.jpg ${i}
    if [[ $? == 2 ]]; then
        echo "${IMGDATE}.jpg is different from ${i}" 
        # do something:
        # cp ${IMGDATE}.jpg ${WORKDIR}/name.jpg
    else
        echo "File is the same as ${i}"
    fi 
done

rm ${TMPDIR}/${IMGDATE}.jpg
```

best ... khay

---

### Post by JCM_Pico on 2012-03-07
Thank you very much Khay.... 

I tough I could compare the find against the /dev/null... I have written wrong in the example I posted 

```
if find ${workdir}*.jpg \( ! -name ${imgdate}.jpg \) -type f -exec diff {} ${imgdate}.jpg \ >/dev/null;
```

> Its really hard to see what your trying to do as comparing a number of  images to one image will always be a question of {n} misses to every  hit. Why do you need to compare all the images in this directory?

I had a script working that compared the last download image with the previous one and it would remove it if equal...
But when it was equal it would remove the file and in the next timestep it had nothing to compare with...

Truly I don't need to compare with all the files just with the files retried previously (the 2nd newest file after the download)...
But since I couldn't find a way to do that I though it would be simpler to compare against every file. If its different from every file that's cool and I keep the file:P  

Thank you once again for spending your time helping me

---

### Post by Khayyam on 2012-03-07
> **JCM_Pico said:**
> I tough I could compare the find against the /dev/null... I have written wrong in the example I posted.

hmmmm ... well, how? You see, true/false has to have whats called a 'return value', so an 'if [[ such and such ]]; then' doesn't get to the "then" unless the test returns true. This same principle applies to commands, each command you issue has a 'return value' (success or failure) .. perhaps the following will best illustrate this:

```
% echo "hello" ; echo $?
hello
0
% ls bigglebogglewoggle ; echo $?
ls: bigglebogglewoggle: No such file or directory
1
% if [[ -d $HOME ]]; then echo $? ; fi
0
% if [[ ! -d bigglebogglewoggle ]]; then echo $? ; fi
0
% if [[ $(uname) = Linux ]]; then echo $? ; fi
0
```So, success exits with a "0" and failure with > 0 (1 or 2) .. so we can check this and use it to perform things based on if the test is true.

```
echo "hello"
if [[ $? == 0 ]]; then
    echo ".. and hello to you too"
fi
```

> **JCM_Pico said:**
> ```
if find ${workdir}*.jpg \( ! -name ${imgdate}.jpg \) -type f -exec diff {} ${imgdate}.jpg \ >/dev/null;
```

That just redirects the output of the command to /dev/null

> **JCM_Pico said:**
> I had a script working that compared the last download image with the previous one and it would remove it if equal...
But when it was equal it would remove the file and in the next timestep it had nothing to compare with...

If you only need to compare one image there is no need for a 'for' loop, all you need do is compare one image with another, if the image is the same rm, if not move it to workdir, then the next time it runs select that image for comparison. 

> **JCM_Pico said:**
> Truly I don't need to compare with all the files just with the files retried previously (the 2nd newest file after the download)... But since I couldn't find a way to do that I though it would be simpler to compare against every file. If its different from every file that's cool and I keep the file.

Name them in a way that identifies them as the last image downloaded and saved, then it easy to refer to the last image as you can use workdir/*last.jpeg. You whould the rename the new one to last and the old to some other (sequencial) name.

> **JCM_Pico said:**
> Thank you once again for spending your time helping me

Your welcome ... best khay

---

