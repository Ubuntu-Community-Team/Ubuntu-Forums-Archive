---
title: "Wrap grep output with quotes"
date: 2012-05-12
forum: General Help
---

### Post by Derek Karpinski on 2012-05-12
I am trying to download a Grateful Dead show from [http://stash.nugs.net/attics/720827_mp3.asp?artist=1&show=246&cmd=shows](http://stash.nugs.net/attics/720827_mp3.asp?artist=1&show=246&cmd=shows)

But, their java download thing won't work.

So, I right clicked on the 'listen' button, and got the .m3u file.

Inside the m3u file are the links to the files I want to download.

So, I entered in terminal:

```
grep 'http://*' ./*.m3u | xargs -n1 wget -i -O -
```

And the songs started downloading.  But wget complained about a single quote.

Sure enough, a file is named:
[http://cryptical.nugs.net/vault/gd/720827/gd720827ii_01_Playin'_in_the_Band.mp3](http://cryptical.nugs.net/vault/gd/720827/gd720827ii_01_Playin'_in_the_Band.mp3)

So, if I wrap double quotes around the file, everything works.

How can I wrap the stdout of grep with quotes before piping it to wget? I'm thinking sed, but I don't know.

Any ideas?

---

### Post by cmont899 on 2012-05-12
how about:

```
for $each in `grep 'http://*' ./*.m3u`; do
    wget -i -O "$each"
done
```or as a oneliner:

```
> for $each in `grep 'http://*' ./*.m3u`; do wget -i -O "$each";done
```

---

### Post by Derek Karpinski on 2012-05-12
> **cmont899 said:**
> how about:

```
for $each in `grep 'http://*' ./*.m3u`; do
    wget -i -O "$each"
done
```or as a oneliner:

```
> for $each in `grep 'http://*' ./*.m3u`; do wget -i -O "$each";done
```


did not work:

```
bash: `$each': not a valid identifier
```

awk was what I needed:
```
grep 'http://*' ./*.m3u | awk '{ print "\""$1"\"" }' | xargs -n1 wget
```

---

### Post by sisco311 on 2012-05-12
> **Derek Karpinski said:**
> 
awk was what I needed:
```
grep 'http://*' ./*.m3u | awk '{ print "\""$1"\"" }' | xargs -n1 wget
```

Ugly. :) So is tr:
```

grep 'http://*' x | tr '\n' '\0' | xargs -0 wget -i -O -

```

BTW awk can do (almost?) anything that grep can do:
```

awk '/http:\/\// { print "\""$1"\"" }' *.m3u

```

I'd use:
```
cat *.m3u | while read -r line; do if [[ "$line" =~ ^http:// ]]; then wget -i -O - "$line"; fi; done
```

BashFAQ 001

---

### Post by cmont899 on 2012-05-12
> **Derek Karpinski said:**
> did not work:

```
bash: `$each': not a valid identifier
```awk was what I needed:
```
grep 'http://*' ./*.m3u | awk '{ print "\""$1"\"" }' | xargs -n1 wget
```

sorry should have been:

```
for each in `grep 'http://*' ./*.m3u`; do     
        wget -i -O "$each" 
done
```

---

### Post by Derek Karpinski on 2012-05-12
> **sisco311 said:**
> Ugly. :) So is tr:
```

grep 'http://*' x | tr '\n' '\0' | xargs -0 wget -i -O -

```BTW awk can do (almost?) anything that grep can do:
```

awk '/http:\/\// { print "\""$1"\"" }' *.m3u

```I'd use:
```
cat *.m3u | while read -r line; do if [[ "$line" =~ ^http:// ]]; then wget -i -O - "$line"; fi; done
```BashFAQ 001

It is fugly.....it worked. I know awk can pretty much replace grep and sed in one command, but I don't know awk at all.  I'm shaky on all this stuff, but it's fun.

Thanks, I'll try out your command, and try to parse it.

---

### Post by Derek Karpinski on 2012-05-12
HAHAHAHA.........all this grep, awk, sed.........waste of keystrokes:

```
wget -i *.m3u
```

Works perfectly!!! :lolflag:

---

### Post by sisco311 on 2012-05-12
> **Derek Karpinski said:**
> HAHAHAHA.........all this grep, awk, sed.........waste of keystrokes:

```
wget -i *.m3u
```

Works perfectly!!! :lolflag:

What's the fun in not using a cannon to kill a fly? :)

---

