---
title: "removing a word in a multiple file starting at the dot extension"
date: 2011-08-23
forum: General Help
---

### Post by jao_madn on 2011-08-23
hi

I would like to ask if someone knows a command or a script on how to rename a multiple file in the directory starting at the end of the filename or at the .extension( i would like to remove the last 11 character before the extension) for example

Below is the result of my command ls inside the directory

> 
BBC_In_footsteps_of_Alexander_the_mountain_20-v3veN2U__3I.mp4
BBC_In_the_footsteps_of_Alexander_Afghanistan_17-thAS28SWKKU.mp4
BBC_In_the_footsteps_of_Alexander_Alexandria_7-rQcjjpRwqw4.mp4
BBC_In_the_footsteps_of_Alexander_army_revolts_26-Jwrl2hPSFWA.mp4
BBC_In_the_footsteps_of_Alexander_Bactria_19-cC5pGsUgyiM.mp4
BBC_In_the_footsteps_of_Alexander_climbing_pir_sar_24-oz0pb-Zycvc.mp4
BBC_In_the_footsteps_of_Alexander_Darius_Dies_13-Pn9nj7rWT60.mp4
BBC_In_the_footsteps_of_Alexander_ending_31-4wW8nJi5tOk.mp4
BBC_In_the_footsteps_of_Alexander_ends_of_earth_22-uMgX_UDHo4g.mp4
BBC_In_the_footsteps_of_Alexander_Gaza_6-pr2mkAgQL9k.mp4
BBC_In_the_footsteps_of_Alexander_gordion_knot_4-5nfmZfEV_wA.mp4
BBC_In_the_footsteps_of_Alexander_Indus_Delta_29-8CiauNRLSUU.mp4
.....> 
BBC_In_footsteps_of_Alexander_the_mountain_20.mp4
BBC_In_the_footsteps_of_Alexander_Afghanistan_17.mp4
The filename has no predefined length or has diff length so starting at the beggining of the filename is not much use.

Im using pyrenamer but the delete option will start counting character at the beggining of the filename and there has no option that will start deleting at the end of after the extension.

Thanks for any input..

---

### Post by papibe on 2011-08-23
It is possible to do it with a bash script, however there's a nice graphical tool that can do that and more. It's called pyRenamer (it is on the Software Center). Can rename a bunch of files at the same time using regular expressions. You can play with the expressions until you see the correct change, and then run it.

Hope it helps,
Regards.

---

### Post by sisco311 on 2011-08-23
In Ubuntu, you can use the perl based rename command:
```
cd /path/to/dir
rename **-n** 's/(.*)-.*.mp4/$1.mp4/' *.mp4
```
Invoked with the -n option it will only show what files would have been renamed.

---

### Post by jao_madn on 2011-08-23
> **papibe said:**
> It is possible to do it with a bash script, however there's a nice graphical tool that can do that and more. It's called pyRenamer (it is on the Software Center). Can rename a bunch of files at the same time using regular expressions. You can play with the expressions until you see the correct change, and then run it.

Hope it helps,
Regards.

Hi papibe. I though used the pyrenamer as i mentioned but i faced the problem in the tab option INSERT?DELETE. The feature starts counts the character from the beginning of the filename as i mention the filename has diff length so therefore one fix count starting from the beginning has some problem. I hope you can explain on how to overcome the problem with the use of regular expression is much helpful

Thanks for the reply

---

### Post by jao_madn on 2011-08-23
> **sisco311 said:**
> In Ubuntu, you can use the perl based rename command:
```
cd /path/to/dir
rename **-n** 's/(.*)-.*.mp4/$1.mp4/' *.mp4
```Invoked with the -n option it will only show what files would have been renamed.


Hi your command is much very helpful but i have some question hope you can make some workaround, I notice you used a "-" field set but a filename that has inside the 11 character i want to delete has "-"  that will read also as field set so it will stop although is useful in my case if only one filename has "-" inside the 11 character but what if it has multiple filename that has the same issue..

Before
BBC_In_the_footsteps_of_Alexander_climbing_pir_sar  _24-oz0pb-Zycvc.mp4

After
BBC_In_the_footsteps_of_Alexander_climbing_pir_sar  _24-oz0pb.mp4

It should be 
BBC_In_the_footsteps_of_Alexander_climbing_pir_sar  _24.mp4

Thanks much for the responce..

---

### Post by sisco311 on 2011-08-23
Oops, sorry I missed that. If there are exactely 11 characters than you can try something like:
```
rename -n 's/^(.*)-.{11}\.mp4$/$1.mp4/' *.mp4
```

EDIT: I also forgot to escape the period (.) before mp4 in my previous code. :redface:

---

### Post by jao_madn on 2011-08-23
> **sisco311 said:**
> Oops, sorry I missed that. If there are exactely 11 characters than you can try something like:
```
rename -n 's/^(.*)-.{11}\.mp4$/$1.mp4/' *.mp4
```EDIT: I also forgot to escape the period (.) before mp4 in my previous code. :redface:


Thanks very much. it solved my problem..

---

### Post by sisco311 on 2011-08-23
You are welcome!

---

### Post by papibe on 2011-08-23
Just for reference: This works on pyRenamer with the list you provided:

```
Patterns Tab

Original file name pattern  {@}_{#}-{@}
Renamed file pattern        {1}_{2}
```
Glad you solved your problem,
Regards.

---

### Post by sisco311 on 2011-08-23
> **papibe said:**
> Just for reference: This works on pyRenamer with the list you provided:

```
Patterns Tab

Original file name pattern  {@}_{#}-{@}
Renamed file pattern        {1}_{2}
```
Glad you solved your problem,
Regards.

Thanks for posting it. I personally don't use any GUI rename tools (like gprename, purrr, gwenrename, krename... or thunar...), but I like to play with them. :)

Thanks again.

---

### Post by jao_madn on 2011-08-25
> **papibe said:**
> Just for reference: This works on pyRenamer with the list you provided:

```
Patterns Tab

Original file name pattern  {@}_{#}-{@}
Renamed file pattern        {1}_{2}
```Glad you solved your problem,
Regards.

Hi Papipe

I check also your tuts in the pyrenamer and works very much fine thanks for the additional info..

---

