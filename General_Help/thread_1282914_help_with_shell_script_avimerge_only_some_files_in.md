---
title: "help with shell script avimerge only some files in dir"
date: 2009-10-04
forum: General Help
---

### Post by neilevan814 on 2009-10-04
Here is what I have....I have had plenty other things and give up.  I don't really know this coding so any suggestions would be a start

This is being run on a directory of 81 files and eventually I would like it to run through three files at a time avimerge them and do it again


#!/bin/bash
num=0
for i in *.avi
do
file[$num]="$i"
if [ $num -le 3 ]
then echo ${file[$num]}
((num++))
else
avimerge -o zone.avi -i ${file[0]}, ${file[1]}, ${file[2]}
fi
done

---

### Post by lloyd_b on 2009-10-05
Here's another take on the code:```
#!/bin/bash

NUM=0
ZONE=1

for CURFILE in *.avi; do
    # If we have 3 files in the array, run avimerge on them
    if [ $NUM -gt 2 ]; then
        echo "Merging: ${file[0]}, ${file[1]}, ${file[2]}"
        avimerge -o zone$ZONE.avi -i ${file[0]}, ${file[1]}, ${file[2]}   
        # Reset the counter back to zero, and increment the ZONE counter
        NUM=0
        ((ZONE++))
    fi
    file[$NUM]="$CURFILE"
    echo "Stored file $CURFILE in array at slot $NUM"
    ((NUM++))
done

# If we have any files left to merge, merge them, even if there aren't 3
if [ $NUM -eq 2]; then
    echo "Merging: ${file[0]}, ${file[1]}, ${file[2]}"
    avimerge -o zone$ZONE.avi -i ${file[0]}, ${file[1]}, ${file[2]} 
elif [ $NUM -eq 1]; then
    echo "Merging: ${file[0]}, ${file[1]}"
    avimerge -o zone$ZONE.avi -i ${file[0]}, ${file[1]}
fi   

```I added that section at the end to handle situations where the number of files is *not* an even multiple of 3.  

I also added the ZONE counter, so that the files won't always be merged to "zone.avi" - instead it'll be "zone1.avi", "zone2.avi", "zone3.avi", etc.  I'm not familiar with "avimerge", so I have no clue what'll happen on the second pass, when "zone1.avi" is one of the input files *and* the specified output file name...

This code has NOT been tested, so use at your own risk.

Lloyd B.

---

### Post by neilevan814 on 2009-10-05
Hi Lloyd,

Thanks it worked perfectly....after I removed the commas between the files in avimerge.
 
I'm running the script now and the bottom half of the script, I think it's that, is merging my merges three at a time....

This program got a little slap happy..

---

### Post by lloyd_b on 2009-10-05
> **neilevan814 said:**
> Hi Lloyd,

Thanks it worked perfectly....after I removed the commas between the files in avimerge.
 
I'm running the script now and the bottom half of the script, I think it's that, is merging my merges three at a time....

This program got a little slap happy..

Thanks for the try, but this is what I got :

Stored file twilight-zone-1-acts-of-terror.avi in array at slot 0
Stored file twilight-zone-22-room-2426.avi in array at slot 1
Stored file twilight-zone-23-the-mind-of-simon-foster.avi in array at slot 2
Merging: twilight-zone-1-acts-of-terror.avi, twilight-zone-22-room-2426.avi, twilight-zone-23-the-mind-of-simon-foster.avi
scanning file twilight-zone-1-acts-of-terror.avi, for video/audio parameter
AVI open: avilib - Error opening AVI file
REASON: No such file or directory

It says it can't do it because there is no such file or directory, but obviously that is not so.  Got any ideas about how avimerge and even cat for that matter are reading these 
files?

I must thank you however for getting me a step closer with the loop structure working on three files at a time.  I will have to study that and learn something.

Well, I just tried to avimerge three of those in the terminal and I am getting the same error message..so may be these files for some reason, although they play just fine.

Hmmm - that output set off an alarm bell. ```
scanning file twilight-zone-1-acts-of-terror.avi[COLOR="Red"],[/COLOR] for video/audio parameter
```Note that comma.  Are you sure you got rid of all the commas for the "avimerge" command?

Lloyd B.

---

### Post by neilevan814 on 2009-10-05
Hi Lloyd,

I think my last message was a little confusing.  I didn't delete all my explanation about the avimerge problem.  I did remove all the commas and your program did exactly what I wanted to, BUT a little bit more-ha-ha...It merged my 9 merges into three of their own.  I'm gonna have a look at it and see if I can fix that.  If I get it working, I'll let you know.  Thanks again.

---

### Post by neilevan814 on 2009-10-08
Here is the finalized script I came up with:

It cycles through a directory of avi files,takes three avi files at a time and merges them. Moves the original unmerged files to a new directory, orig_files, performs avimerge and avi sync on the merged files. Cleans up unnecessary files.

#!/bin/bash

declare -i N=0			# declare -? is optional
declare -a FILES=()
declare -i zone=0
mkdir orig_files
origcnt=`ls  | grep .avi | wc -l`

curcnt=`ls orig_files | grep .avi | wc -l`

for A in *.avi; do
	echo "$A"		# optional
        test $(($origcnt - $curcnt)) -ge 3
  
        if [[ $(( ++N )) -eq 3 ]]; then		# not sure if it's same as '[[ ++N -eq 3'
		N=0
                ((++zone))
		avimerge -o zone"$zone".avi -i "${FILES[1]}" "${FILES[2]}" "$A"
                avisync -i zone"$zone".avi -o "ZONE"$zone".avi" -n -5
                rm zone"$zone".avi		# do we need the commas?
                mv "${FILES[1]}" orig_files/"${FILES[1]}"
                mv "${FILES[2]}" orig_files/"${FILES[2]}"
                mv "$A" orig_files/"$A"
                
	else
		FILES[N]=$A
                          
        fi

done



((++zone))
test $(($origcnt - $curcnt)) -lt 3  

if [[ N -eq 1 ]]; then
        
	avimerge -o zone"$zone".avi -i "${FILES[1]}"
       avisync -i zone"$zone".avi -o ZONE"$zone".avi -n -5
       rm zone"$zone".avi              # do we need the commas?
             mv "${FILES[1]}" orig_files/"${FILES[1]}"
                
elif [[ N -eq 2 ]]; then
	avimerge -o zone.avi -i "${FILES[1]}" "${FILES[2]}"
         avisync -i zone"$zone".avi -o ZONE"$zone".avi -n -5
         rm zone"$zone".avi              # do we need the commas?
                mv "${FILES[1]}" orig_files/"${FILES[1]}"
                mv "${FILES[2]}" orig_files/"${FILES[2]}"

fi

echo "Done"
exit 0

---

### Post by lloyd_b on 2009-10-08
Hmmm - as far as I can tell, the variables "origcnt" and "curcnt" aren't actually doing anything.  Neither is updated after they are originally set, and the "test $(($origcnt - $curcnt)) -ge 3" lines don't actually affect anything (it performs the comparison, returning true/false, but this return value is never used).

A note: "test $(($origcnt - $curcnt)) -ge 3" and "[[ $(($origcnt - $curcnt)) -ge 3 ]]" do *exactly* the same thing - the bracket form is a shorthand for the "test".  Also note that you can use single brackets ("[ $(($origcnt - $curcnt)) -ge 3 ]") and accomplish the same thing - the double brackets do offer some advantages (read [here]("http://www.ibm.com/developerworks/library/l-bash-test.html") for details) but I don't believe you need any of them in this code).

A final note - when posting code to the forums, it's best to enclose it in CODE tags (highlight the text, and click the "#" icon above the message entry area).  This preserves any formatting, especially indentation, which makes code MUCH easier to read.

Lloyd B.

---

