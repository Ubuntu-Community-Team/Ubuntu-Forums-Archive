---
title: "Passing Arrays"
date: 2006-05-25
forum: General Help
---

### Post by bluemike807 on 2006-05-25
Hi, Im not sure if this falls within the auspices of this forum but Im having a problem and can't find the solution.

I've made a little script which spawns a series of subscripts and captures their PIDs upon creation in an array.
Ideally, I want to be able to pass this array as an argument to C++ program I've made to govern the operation of these subscripts. 

My problem is, I dont know how to pass arrays from scripts as arguments for the next script/program.

Help?

---

### Post by stevestyle51 on 2006-05-25
Could you submit a quick snippet of your code that the array is in?  I think that you can associate the destination file with the file that the array is actually in.  You need to allococate the memory for the array and then you can pass it to the other script as an object, I think.  So pass me some code and I'll try and help.

---

### Post by ifokkema on 2006-05-25
[QUOTE=bluemike807]My problem is, I dont know how to pass arrays from scripts as arguments for the next script/program.[/QUOTE]

Hi,

Can't you just run the C program with the PIDs as the arguments?
```
/my/program pid1 pid2 pid3 pid4 ...
```
Then you can make your C program read the PIDs from the argv array.

HTH,

Ivo

---

### Post by bluemike807 on 2006-05-25
There's not really all that much to show, what Im doing is really no more advanced than:

A=0
while [ $A -lt 10 ]
do
        ./subscript.sh 
        let "PS[$A]=$!"
	let "A=A+1"
done
./thirdscript <Array as Argument>

---

### Post by bluemike807 on 2006-05-25
[QUOTE=ifokkema]Hi,

Can't you just run the C program with the PIDs as the arguments?
```
/my/program pid1 pid2 pid3 pid4 ...
```
Then you can make your C program read the PIDs from the argv array.

HTH,

Ivo[/QUOTE]

I suppose I could but for this program Im passing four arguments in total, two of which are arrays of variable length - each of which contains PIDs for two separate types of programs, so I cant distinguish between the two if I just pass them individually. 
Also I dont really want to have to supply additional 'count' arguments showing how many elements / array.

Well, I suppose I've just answered my own question. I can do it that way and its not entirely impractical. 
But is there no clean cut way to just pass the entire array between forms?

---

