---
title: "Bash function issue"
date: 2012-09-08
forum: General Help
---

### Post by Primefalcon on 2012-09-08
I have the following function in a bash script that keeps throwing me an error... not sure exactly what is going on here.

it keeps saying error near unexpected token fi line 10

```

#!/bin/bash

function convertEps()
{
cd "~/Music/gpodder-downloads/$1"
for f1 in *.mp4; do
f2="${f1%.mp4}.mpeg"
if [ ! -f Rockbox/$f2 ] then
avconv -i "$f1" -r 20 -s 166x96 -b 128k "Rockbox/${f1%.mp4}.mpeg"
fi
done
}

convertEps('first folder to do');
convertEps('second folder to do');

```

---

### Post by Vaphell on 2012-09-08
```
if [ ! -f Rockbox/$f2 ][COLOR="Red"];[/COLOR] then
```

before then (if) and do (for/while) there needs to be ; (unless you move them to the next line)

---

### Post by Primefalcon on 2012-09-08
> **Vaphell said:**
> ```
if [ ! -f Rockbox/$f2 ][COLOR="Red"];[/COLOR] then
```

before then (if) and do (for/while) there needs to be ; (unless you move them to the next line)
grrrr php, javascript, c++ and now bash I spend ages trying to work something out for it to be a missing semicolon.................. grrrrr



thank you btw

---

### Post by Primefalcon on 2012-09-08
Ok after a bit more hacking away I got the script working with, btw its a simple conversion script that I put together for my podcasts I listen to... to convert them to a format suitable for the Ipod nano I have running Rockbox

```
#!/bin/bash

convertEp()
{
	cd "$HOME/Music/gpodder-downloads/$1"

	for f1 in *.mp4; do
		f2="${f1%.mp4}.mpeg"
		
		if [ ! -f "Rockbox/$f2" ]; then 
			avconv -i "$f1" -s 176x100 -vcodec mpeg2video -b 229k -ab 192k -ac 2 -ar 44100 -acodec libmp3lame "Rockbox/${f1%.mp4}.mpeg"
		fi
	done
}

convertEp 'podcast 1 folder'
convertEp 'podcast 2 folder'
#and so on

```

---

