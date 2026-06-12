---
title: "Record memory usage of program?"
date: 2010-01-17
forum: General Help
---

### Post by djeyewater on 2010-01-17
Is there a way I can start a program and then record a log of how much memory it's using at a specific interval until the program ends?

I've tried writing a shell script but get the error:
./apps/mem-test.sh: line 4: [: too many arguments

Here's the non-working script:
```
$HOME/apps/ImageMagick/bin/convert -limit memory 64 -limit map 128 $HOME/SSI/davidkennardphotography/Img-Orig/95-Pole-Bank.jpg -set option:filter:filter Lanczos -set option:filter:blur 0.8 -resize 1024x720 $HOME/resizedImage.jpg &
GOODY="ps -p $! -o pid,%cpu,rss,cmd | grep convert >>test.txt"

 while [ $GOODY -ne '' ]
 do
   sleep 0.5
 done
```

Thanks

Dave

---

### Post by kidders on 2010-01-18
Hi there,

Something like this ought to do the trick ...

```
#!/bin/bash
$HOME/apps/ImageMagick/bin/convert -limit memory 64 -limit map 128 $HOME/SSI/davidkennardphotography/Img-Orig/95-Pole-Bank.jpg -set option:filter:filter Lanczos -set option:filter:blur 0.8 -resize 1024x720 $HOME/resizedImage.jpg &
CMD_PID=$!

if [ $? -eq 0 ]; then
	while [ $? -eq 0 ]; do
		sleep 2
		ps --no-headers -p $CMD_PID -o pid,%cpu,rss,cmd >> test.txt
	done
fi
```

In your version, the error on line 4 would be solved by quoting $GOODY, but you'd only get one log entry out of it.

I hope that helps.

---

### Post by djeyewater on 2010-01-22
Yep, that does the trick. Thanks for the help!

Dave

---

### Post by altonbr on 2010-12-11
This is very useful, thank you!

---

