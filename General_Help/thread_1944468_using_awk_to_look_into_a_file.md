---
title: "using awk to look into a file"
date: 2012-03-21
forum: General Help
---

### Post by fra11 on 2012-03-21
Dear all,
I'm trying to use awk into an if clause to look into a file and use the information there to run a command from an external program. Basically I need to look into a file that is made of 2 numerical columns and I need to assign for each line the value of each column to a variable to use later into an external command. 
My code is 
```

for ((j=1; j=2; j++))
do
snapshoot=`awk '{$2 &&  NR==$j}' xtc_file.txt`
trajectory=`awk '{$1 && NR==$j}'  xtc_file.txt`
snapshot_fin=`expr $snapshoot + 1`
echo $snapshot $trajecory $snapshot_fin

  /home/cocktail/vitalini/gromacs_special/bin/trjconv -f /home/cocktail/noe/my_papers/dynamin-dimer/sims/analysis/allsims/300-$j.xtc -s ../../starting_files/dynamin_dimer_cg.gro -o ../cg_gro/300-$j-$snapshoot.gro  -center -b $snapshoot -e $snapshoot_fin

done

```

but despite the file looks like 

```

26      1
26      2
26      3
26      4
26      5
26      6
26      7
26      8
26      9
26      10
26      11
26      12
26      13
26      14
26      15
26      16
26      17


```

What I get as a result of the echo command is a sequence of 1. 
Can anyone help me to use awk to assign values to a variable? Or if anyone has a better suggestion on how to solve this problem I would really appreciate that.
Thanks!
Fra

---

### Post by codemaniac on 2012-03-21
what is ```
for ((j=1; j=2; j++))
```?
you are having infinite loop because of no terminating condition .

---

### Post by codemaniac on 2012-03-21
you have also misspelled variable **trajectory ** and **snapshot **.
multiple glitches can be found in your source code .
try something like below .

```
for ((j=1; j<=2; j++))
do
snapshot=`awk -v no=$j 'NR==no{print $2}'  xtc_file.txt`
trajectory=`awk -v no=$j 'NR==no{print $1}'  xtc_file.txt`
snapshot_fin=`expr $snapshoot + 1`
echo "$snapshot $trajectory $snapshot_fin"
done
```

---

### Post by fra11 on 2012-03-21
Yes I was having an infinite loop and I have corrected it, however I still have the problem that the value into the file is not assigned to the variable through awk in fact my code now looks like

```

for ((j=1; j<=2; j++))
do
snapshoot=`awk '{$2 &&  NR==$j}' xtc_file.txt`
trajectory=`awk '{$1 && NR==$j}'  xtc_file.txt`
snapshot_fin=`expr $snapshoot + 1`
echo 'snapshot is' $snapshot 
echo 'trajectory is' $trajecory 
echo 'snapshoot_fin is' $snapshot_fin

#  /home/cocktail/vitalini/gromacs_special/bin/trjconv -f /home/cocktail/noe/my_papers/dynamin-dimer/sims/analysis/allsims/300-$j.xtc -s ../../starting_files/dynamin_dimer_cg.gro -o ../cg_gro/300-$j-$snapshoot.gro  -center -b $snapshoot -e $snapshoot_fin

done


```

but the output is

```

snapshot is
trajectory is
snapshoot_fin is 1
snapshot is
trajectory is
snapshoot_fin is 1


```

Can you help me on that please?
Thank you so much
Fra

---

### Post by codemaniac on 2012-03-21
try something like below my dear pal .

```
for ((j=1; j<=2; j++))
do
snapshot=`awk -v no=$j 'NR==no{print $2}'  xtc_file.txt`
trajectory=`awk -v no=$j 'NR==no{print $1}'  xtc_file.txt`
snapshot_fin=`expr $snapshoot + 1`
echo "$snapshot $trajectory $snapshot_fin"
```
done

---

### Post by fra11 on 2012-03-21
Thank you very much! it worked!!! :guitar:

---

