---
title: "Bash script to recurse directories and exec ffmpeg using find (possibly)"
date: 2010-10-03
forum: General Help
---

### Post by excetara2 on 2010-10-03
I wrote a script that easily runs it in the same directory as it was run below:

#for f in *.MTS ;
#do ffmpeg -i "$f" -acodec copy -vcodec libx264 -threads 2 -deinterlace -vpre slow -b 20000k -bt 3000k -refs 4 "${f%.MTS}.mp4" ; 
#done



I want to be able to use the find command so it will recurse through all the videos in my videos folder. Is there a painless way to do this. Here is the start of my find command but it doesn't work. Any help appreciated:

find . -name "*.MTS" -exec ffmpeg -i 'basename{}' -acodec copy -vcodec libx264 -threads 2 -deinterlace -vpre slow -b 20000k -bt 3000k -refs 4 'basename{%.MTS}.mp4'

---

### Post by abhi2706 on 2010-10-03
From this command, I understand that you are trying to do operation on *MTS files and save them with MP4 extension. If I am right, then check try following::


find . -name "*.MTS" -exec ffmpeg -i `basename {}` -acodec copy -vcodec libx264 -threads 2 -deinterlace -vpre slow -b 20000k -bt 3000k -refs 4 {}.mp4 \;


I am not sure about second basename usage that is why I have removed from command line.

---

### Post by excetara2 on 2010-10-03
Got it working with the below script.

find . -name "*.MTS" -exec ffmpeg -i '{}' -acodec copy -vcodec libx264 -threads 2 -deinterlace -vpre slow -b 20000k -bt 3000k -refs 4 {}.mp4 \;

But the files are named blah.MTS.mp4. How do I remove the .MTS. I had used .%MTS before but couldn't figure out how to get it to work with this. Also thought of running the sed command like below but it doesn't work. Not sure if you can put two exec statements or the proper way to do this.


find . -name "*.MTS" -exec ffmpeg -i '{}' -acodec copy -vcodec libx264 -threads 2 -deinterlace -vpre slow -b 20000k -bt 3000k -refs 4 -exec sed -e 's/.MTS/.mp4/' {} \;

Cheers and thanks for the help.

---

### Post by abhi2706 on 2010-10-03
Two "exec" command will work on find but

1. The argument for both of them will be same because of scope.
2. "sed 's/.MTS/.mp4/' {}" will work on the content of file rather than on the name. So, it is just dangerous to do that.

If I get something for renaming in one line, then I will come back.

---

### Post by abhi2706 on 2010-10-03
To run 2 exec in find, run the command with following syntax:


find . -name "*MTS" -exec "Command 1" \; -exec "Command 2" \; More Command \;

---

### Post by excetara2 on 2010-10-03
I can run two separate find commands then but what is the best way to search and replace *.MTS.mp4 with *.mp4.

Will the sed command work or should I use some other command?? Provide a quick example?? I've been trying to figure this out.

Thanks again

---

### Post by nothingspecial on 2010-10-03
To rename the ones you`ve done already
```

 rename 's/\.MTS\.mp4$/\.mp4/' *.mp4
```

Test it first, I may have made a typo. :)

---

### Post by excetara2 on 2010-10-03
That is correct. How do I run that recursively through the directory structure like the find command. The find goes into my video folders and changes the .MTS files. Then I want that to do the same but currently only works in the current folder.

Can I put that into the exec command in find somehow?? I tried but couldn't figure it out.


Thanks for the help so far.

---

### Post by excetara2 on 2010-10-03
Got it working!!!!

Execute with: 

#find . -type d -exec MTStomp4.sh "{}" \;




Made a .sh and added a link to the bin as MTStomp4.sh:

if [ -d "${1}" ] ; then
  cd "${1}"
else
  echo "Error: bad argument. Expected a valid directory name for the first argument"
  echo "Bad directory name = ${1}"
  exit 1
fi

for f in *.MTS ;
do ffmpeg -i "$f" -acodec copy -vcodec libx264 -threads 2 -deinterlace -vpre slow -b 20000k -bt 3000k -refs 4 "${f%.MTS}.mp4" ; 
done


Cheers

---

