---
title: "Accessing and creating files names with nested loop in Bash"
date: 2011-08-12
forum: General Help
---

### Post by Yusufkhan on 2011-08-12
[B][SIZE=2]hi! can anyone please help with nested loop in ''Bash-Scripting in Linux'' ?
What's wrong with my code:

for  x  in `seq 0.75 0.01 0.95` 
do
 for  y  in `seq 0.20 0.01 0.40`    
 do
  grep flux1: memb0_$x_$y.out > mem-flux0_$x_$y.dat
 done
done[/SIZE][/B]

[SIZE=2] [/SIZE][SIZE=2]it should grep flux1 from ''memb0_0.75_0.20.out'' to the output file ''mem-flux0_0.75_0.20.dat'&#8203;' and so on according to changing loop values but it's not doing so.
Rather  it only names the file like ''mem-flux_0.75'' or ''mem-flux_0.20'' and  keep on overwriting the generated files as the loops proceed.

 How can man assign nested loop values to output file name ? 

Thanks
[/SIZE][SIZE=2]

[/SIZE]

---

### Post by scottstensland on 2011-08-12
this works :

grep flux1 memb0_${x}_${y}.out > mem-flux0_${x}_${y}.dat

basically you do not need that : after your grep search string
and make the shell variables $x  into ${x}

enjoy - scott stensland

---

