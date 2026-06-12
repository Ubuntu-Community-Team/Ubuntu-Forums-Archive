---
title: "Several scripts simultaneously accessing one file"
date: 2010-01-21
forum: General Help
---

### Post by Andreas1 on 2010-01-21
Hi,

I made a script for batch processing brain scans (with FreeSurfer). I have a batch file stored on an NFS server that looks something like this:

```
subject1
subject2
subject3
subject4

```
now my script is performed on several computers at a time, first it marks an item to be in use (with sed -i 's/.../...'), then processes it (it gets the actual subject files from elsewhere on the server, then puts them back), then marks it to be finished in the list. so during action the batch file should look something like this:

```
subject1 finished
subject2 inprogress on host1
subject3 inprogress on host2
subject4
```


so i tried a run and watched the batch file, now i observed something like this:

```
subject1 finished
[COLOR="Red"]subject2 inprogress on host1[/COLOR]
subject3 inprogress on host2
[COLOR="Red"]subject4 inprogress on host1[/COLOR]
subject5

```

this should not be possible, there was only one script running on host1. the subjects never got marked as finished, although i know for a fact that they were finished. also, the script sometimes seemed to hang for moments. could this be a problem with simultaneous access to that file, and if so, what can i do?

---

### Post by falconindy on 2010-01-21
Post your script, please.

---

### Post by pbrane on 2010-01-21
As falconindy has pointed out it would be hard to answer your question without seeing the actual script. However if you are accessing files concurrently and changing the file status (in-use, finished, etc) then you need to protect the 'status' of that file from being changed by script two during an operation by script one.

---

### Post by Andreas1 on 2010-01-21
this is the relevant part of the script:```
	run="true"
	while [ "$run" = "true" ]
	do
		for subject in $(cat $list)
		do
			# If subject is not marked to be in progress or finished
			if [ "$(grep -w $subject $list)" = "$subject" ]
			then
				# mark subject to be in progress
				sed -i "s/$(grep -w $subject $list)/$subject inprogress on $HOSTNAME/" $list
				
				# RUN RECON_ALL_SUBJECT
				recon_all_subject
				
				# then mark subject as finished
				sed -i "s/$(grep -w $subject $list)/$subject finished/" $list
				
				
				
				# break: start list from top again, in case it got changed
				run="true"
				break
			else
				# continue with next subject and finish unless above is true again
				run="false"
				continue
			fi
		done
	done 2>>errorlog

```
maybe i should add that i am somewhat new to bash scripts (and programming in general, for that matter).
also, just added this, stderr from the above:
```
grep: list: Permission denied
dle
sed: read error on list: Stale NFS file handle
grep: list: Permission denied
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: syntax error
r 0: no previous regular expression
(standard_in) 1: syntax error
grep: list: Stale NFS file handle
sed: -e expression #1, char 0: no previous regular expression
(standard_in) 1: syntax error
grep: list: Stale NFS file handle
grep: list: Stale NFS file handle
previous regular expression
sed: -e expression #1, char 0: no previous regular expression
(standard_in) 1: syntax error
grep: list: Stale NFS file handle
sed: -e expression #1, char 0: no previous regular expression
sed: -e expression #1, char 0: no previous regular expression
(standard_in) 1: syntax error
(standard_in) 1: syntax error
grep: list: Stale NFS file handle
sed: -e expression #1, char 0: no previous regular expression
grep: list: Stale NFS file handle
sed: -e expression #1, char 0: no previous regular expression
(standard_in) 1: syntax error
grep: list: Stale NFS file handle
sed: -e expression #1, char 0: no previous regular expression
sed: -e expression #1, char 0: no previous regular expression
(standard_in) 1: syntax error
(standard_in) 1: syntax error
grep: list: Stale NFS file handle
sed: -e expression #1, char 0: no previous regular expression
grep: list: Stale NFS file handle
sed: -e expression #1, char 0: no previous regular expression
(standard_in) 1: syntax error
(standard_in) 1: syntax error
grep: list: Stale NFS file handle
sed: -e expression #1, char 0: no previous regular expression
(standard_in) 1: syntax error
grep: list: Stale NFS file handle
sed: -e expression #1, char 0: no previous regular expression
sed: -e expression #1, char 0: no previous regular expression
(standard_in) 1: syntax error
(standard_in) 1: syntax error
grep: list: Stale NFS file handle
sed: -e expression #1, char 0: no previous regular expression
grep: list: Stale NFS file handle
sed: -e expression #1, char 0: no previous regular expression
(standard_in) 1: syntax error
grep: list: Stale NFS file handle
sed: -e expression #1, char 0: no previous regular expression
sed: -e expression #1, char 0: no previous regular expression
(standard_in) 1: syntax error
grep: list: Stale NFS file handle
sed: -e expression #1, char 0: no previous regular expression
sed: -e expression #1, char 0: no previous regular expression
(standard_in) 1: syntax error
grep: list: Stale NFS file handle
sed: -e expression #1, char 0: no previous regular expression
sed: -e expression #1, char 0: no previous regular expression
(standard_in) 1: syntax error
grep: list: Stale NFS file handle
sed: -e expression #1, char 0: no previous regular expression
sed: -e expression #1, char 0: no previous regular expression
(standard_in) 1: syntax error
grep: list: Stale NFS file handle
sed: -e expression #1, char 0: no previous regular expression
sed: -e expression #1, char 0: no previous regular expression
(standard_in) 1: syntax error
grep: list: Stale NFS file handle
sed: -e expression #1, char 0: no previous regular expression
(standard_in) 1: syntax error
grep: list: Stale NFS file handle
sed: -e expression #1, char 0: no previous regular expression
sed: -e expression #1, char 0: no previous regular expression
(standard_in) 1: syntax error
grep: list: Stale NFS file handle
sed: -e expression #1, char 0: no previous regular expression
(standard_in) 1: syntax error
grep: list: Stale NFS file handle
sed: -e expression #1, char 0: no previous regular expression
(standard_in) 1: syntax error
(standard_in) 1: syntax error
```

if only 1 host is processing, stderr contains only this:

```
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: syntax error

```


EDIT: so it seems i have a problem with NFS file access AND a syntax error. i would be glad about suggestions on both ;-)
EDIT4: no, just noticed the syntax error is from the invoked recon-all. forget it.


EDIT2:
i suppose if i use separate lists like: echo "subject1" >> inprogress.list i would get the same access problems.

however, i could do: echo "inprogress" >> subject1, what do you think? (apart from the mess with all those empty files)

EDIT3: yes, i am definitely going with that last option for now. file systems are for parallel access, text files not so much. here's the new script:```
	run="true"
	while [ "$run" = "true" ]
	do
		for subject in $(cat $list)
		do
			# If there is no file indicating subject is in progress or finished
			if [ ! -f $subject ]
			then
				# make a file indicating subject is in progress
				echo -e "$(date): in progress on $HOSTNAME" >> $subject
				
				# RUN RECON_ALL_SUBJECT
				recon_all_subject
				
				# add a line indicating subject is finished
				echo -e "$(date): finished on $HOSTNAME" >> $subject
				
				
				
				# break: start list from top again, in case it got changed
				run="true"
				break
			else
				# continue with next subject and finish unless above is true again
				run="false"
				continue
			fi
		done
	done

```

---

### Post by john newbuntu on 2010-01-21
Well, as you may know, scripts can be written in different ways.  I'll not get into the logic too much. I'm sure it'll be a good experience for you to become an expert in scripting.

However, when it comes to concurrent (same time) file access from different scripts, one of the mechanisms that you might want to implement is a "lock" file (lets call it .lock).  This is a file in the same directory as your subject files.

Now every process that tries to get a file should select a file only if it does not see the .lock file.   If it does, then it needs to wait/sleep in a loop until it does not see the .lock file.  If it fails to see the .lock file, then it creates the .lock file, chooses the next file to process, removes the .lock file and goes on its way.  This way, you are serializing your access to the data directory and there is no repetitive work.  There are some holes in the logic that I mentioned, which you can think debug later.

Also remember that these processes can not loop on forever (unless you want it to run it as a server).  So you need to either set a limit on a loop to terminate the process

Now, for whatever reason, the file subject1 is unable to get processed, it should be marked with a different suffix so that no other process will pick it up.

---

