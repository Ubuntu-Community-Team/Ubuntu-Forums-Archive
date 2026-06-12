---
title: "Quick way to find images (Batch Script)?"
date: 2012-04-15
forum: General Help
---

### Post by Bstfmg on 2012-04-15
Hey,

I'm back from backpacking with my dual Ubuntu/Windows dual boot (3x partitions). I dumped all my pictures from my trip on the Ubuntu partition using F-Spot, however as my disk space became full, I put them in random places on my C: and D: drives. I'm not trying to find all images, and index them using F-Spot so I can burn them to disk. I think I can manually find them, but does anyone have any suggestions of a less tedious way? I'm thinking of some sort of batch script where I add all the directories I find images in and it will put them in order (DFSC00001 - DFSC99999) and spot any missing ranges? 

Thanks!

---

### Post by Vaphell on 2012-04-15
```
find /media/dir1 /media/dir2 ~/whatever -iname 'dfsc*.jpg' > pics.txt
sed -r 's:^.*/[^/0-9]*([0-9]+)[^/0-9]*$:\1:' pics.txt | sort > sorted.txt
x=-1; while read n; do if ((10#$n-10#$x>1)); then printf "%04g-%04g\n" $((10#$x+1)) $((10#$n-1)); fi; x=$n; done < sorted.txt
```

---

### Post by Bstfmg on 2012-04-15
> **Vaphell said:**
> ```
find /media/dir1 /media/dir2 ~/whatever -iname 'dfsc*.jpg' > pics.txt
sed -r 's:^.*/[^/0-9]*([0-9]+)[^/0-9]*$:\1:' pics.txt | sort > sorted.txt
x=-1; while read n; do if ((10#$n-10#$x>1)); then printf "%04g-%04g\n" $((10#$x+1)) $((10#$n-1)); fi; x=$n; done < sorted.txt
```
Thank you! 

Three more questions: 

1) Could you please edit the above so it lists the full directories of each image in the sorted.txt file?
2) Any automated way to detect any missing image?
3) Finally, any image over 9999 isn't shown, any way of modifying the script so that 10000+ can be included?

thanks again!

---

### Post by Vaphell on 2012-04-16
```
find dir1 dir2 dir3 -iname 'dscf*.jpg' | sed -r 's:^.*/[^/0-9]*([0-9]+)[^/0-9]*$:\1   &:' | sort -n > sorted.txt
x=-1; xf=''; while read n nf; do if ((10#$n-10#$x>1)); then printf "%04g-%04g  %s %s\n" $((10#$x+1)) $((10#$n-1)) "$xf" "$nf"; fi; x=$n; xf="$nf"; done < sorted.txt
```

i added existing files that define the missing range, eg 0000.jpg and 0100.jpg will show up next to the 0001-0099 range.

are you sure there are more than 4 digits? assuming FAT storage you have a 8.3 naming convention. DFSC takes 4 spots, 4 left for digits.
it's easy to check though
```
grep -E '[0-9]{5}' sorted.txt
```
if there are series of 5 digits in sorted.txt it will find them.
nothing in these commands assumed 4 digits, well maybe except padding with 0s but it would work either way, should the 5digit numbers exist.
```
$ printf "%04g  %04g\n" 33 33333
0033  33333
```

---

