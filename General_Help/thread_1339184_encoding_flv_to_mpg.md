---
title: "encoding flv to mpg"
date: 2009-11-27
forum: General Help
---

### Post by sr_guy on 2009-11-27
I'm looking to encode multiple FLV files at once, but want to keep the original flv filname.

i.e.

ffmpeg -i *.flv -ab 56 -ar 22050 -b 500 -s 320x240 [mpg]

so, I want to encode every FLV file in a particular directory to mpg, and keep it's original filename in the mpg file.

---

### Post by sedawk on 2009-11-27
```

for FILE in *flv;do 
  echo "ffmpeg -i $FILE -ab 56 -ar 22050 -b 500 -s 320x240 ${FILE%.flv}.mpg"
done

```

If the output looks good you can either redirect the output
to a new script like do_conversion.sh or you can
remove the echo and hyphens to really do the thing instead
of only printing what it would do.

---

