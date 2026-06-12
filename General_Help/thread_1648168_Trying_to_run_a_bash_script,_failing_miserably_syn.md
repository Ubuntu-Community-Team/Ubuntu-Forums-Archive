---
title: "Trying to run a bash script, failing miserably: syntax error near unexpected token"
date: 2010-12-18
forum: General Help
---

### Post by carn1x on 2010-12-18
Ok, so I thought I'd make myself a bash script of sorts to download movie trailers, from a file where I manually dump the URL of each file on a separate line:

file 'trailerlist':
> [http://trailers.apple.com/movies/independent/bandbaajabaaraat/bandbaajabaaraat-tlr1_h640w.mov](http://trailers.apple.com/movies/independent/bandbaajabaaraat/bandbaajabaaraat-tlr1_h640w.mov)
[http://trailers.apple.com/movies/independent/badwriting/badwriting-tlr1_h480p.mov](http://trailers.apple.com/movies/independent/badwriting/badwriting-tlr1_h480p.mov)
[http://trailers.apple.com/movies/independent/plasticplanet/plasticplanet-tlr1_h480p.mov](http://trailers.apple.com/movies/independent/plasticplanet/plasticplanet-tlr1_h480p.mov)
[http://trailers.apple.com/movies/independent/nenette/nanette-tlr1_h480p.mov](http://trailers.apple.com/movies/independent/nenette/nanette-tlr1_h480p.mov)
[http://trailers.apple.com/movies/independent/philochs/philochs-tlr1_h480p.mov](http://trailers.apple.com/movies/independent/philochs/philochs-tlr1_h480p.mov)
[http://playlist.yahoo.com/makeplaylist.dll?sid=119115442&sdm=web&pt=rd](http://playlist.yahoo.com/makeplaylist.dll?sid=119115442&sdm=web&pt=rd)
[http://trailers.apple.com/movies/independent/takemehometonight/takemehometonight-tlr1_h480p.mov](http://trailers.apple.com/movies/independent/takemehometonight/takemehometonight-tlr1_h480p.mov)
[http://playlist.yahoo.com/makeplaylist.dll?sid=119167908&sdm=web&pt=rd](http://playlist.yahoo.com/makeplaylist.dll?sid=119167908&sdm=web&pt=rd)
[http://playlist.yahoo.com/makeplaylist.dll?sid=119170600&sdm=web&pt=rd](http://playlist.yahoo.com/makeplaylist.dll?sid=119170600&sdm=web&pt=rd)
[http://trailers.apple.com/movies/independent/asomewhatgentleman/asomewhatgentleman-tlr1_h480p.mov](http://trailers.apple.com/movies/independent/asomewhatgentleman/asomewhatgentleman-tlr1_h480p.mov)
[http://trailers.apple.com/movies/independent/summerwars/summerwars-tlr1_h480p.mov](http://trailers.apple.com/movies/independent/summerwars/summerwars-tlr1_h480p.mov)
[http://trailers.apple.com/movies/fox_searchlight/treeoflife/treeoflife-tlr_h480p.mov](http://trailers.apple.com/movies/fox_searchlight/treeoflife/treeoflife-tlr_h480p.mov)
[http://trailers.apple.com/movies/fox/waterforelephants/waterforelephants-tlr1_h480p.mov](http://trailers.apple.com/movies/fox/waterforelephants/waterforelephants-tlr1_h480p.mov)
[http://playlist.yahoo.com/makeplaylist.dll?sid=119271710&sdm=web&pt=rd](http://playlist.yahoo.com/makeplaylist.dll?sid=119271710&sdm=web&pt=rd)
[http://trailers.apple.com/movies/independent/limitless/limitless-tlr1_h480p.mov](http://trailers.apple.com/movies/independent/limitless/limitless-tlr1_h480p.mov)
[http://trailers.apple.com/movies/independent/hoodtocoast/hoodtocoast-tlr1_h480p.mov](http://trailers.apple.com/movies/independent/hoodtocoast/hoodtocoast-tlr1_h480p.mov)


And then in .bash_aliases:

> alias downtrail="for i in `cat ./trailerlist`;do wget -U 'QuickTime/7.6.2' $i;done"


Finally, the error:

> bash: syntax error near unexpected token `[http://trailers.apple.com/movies/independent/badwriting/badwriting-tlr1_h480p.mov](http://trailers.apple.com/movies/independent/badwriting/badwriting-tlr1_h480p.mov)'

Any ideas chaps?

Apologies if this answered elsewhere on the forums, but each instance I can find relating to this error seems to be specific to each script.

Thanks in advance! In the meantime, I'm gonna go find a bash scripting book :)

---

### Post by gmargo on 2010-12-18
Try it as a function:

```

downtrail()
{
    for i in `cat ./trailerlist`
    do 
        wget -U 'QuickTime/7.6.2' $i
    done
}

```

---

### Post by carn1x on 2010-12-18
> **gmargo said:**
> Try it as a function:

```

downtrail()
{
    for i in `cat ./trailerlist`
    do 
        wget -U 'QuickTime/7.6.2' $i
    done
}

```

Yes your function seems to be running fine thanks a bunch :). Still, a little frustrating I didn't solve the error, but I've got my book now so I'm sure I'll figure it out eventually :)

Thanks again!

---

### Post by hakermania on 2010-12-18
another one:
```

#!/bin/sh
lines=`wc -l < /home/$USER/file_with_trailer_list`
b=1
while [ $b -le $lines ]; then
trailer=$(sed -n "${b}p;${b}q" /home/$USER/file_with_trailer_list)
wget $trailer
b=`expr $b + 1`
done

```

---

### Post by carn1x on 2010-12-18
> **hakermania said:**
> another one:
```

#!/bin/sh
lines=`wc -l < /home/$USER/file_with_trailer_list`
b=1
while [ $b -le $lines ]; then
trailer=$(sed -n "${b}p;${b}q" /home/$USER/file_with_trailer_list)
wget $trailer
b=`expr $b + 1`
done

```

I hope to understand this someday soon :)

---

### Post by hakermania on 2010-12-18
It gets then number of lines of the file with the trailer list, then sets to the variable 'trailer' each line (first line 1(because b=1)) then downloads the first trailer, then it adds 1 to b and reads the 2nd line of the file and downloads the 2nd trailer and so on till 'b' becomes larger than 'lines'
Edit: A little correction: while []; _**do**_ no *while []; then*
thx

---

### Post by gmargo on 2010-12-18
> **carn1x said:**
> Still, a little frustrating I didn't solve the error!

There's really no error to solve.  Bash aliases are quite limited and are essentially for substituting fixed strings.  In general, unless it's an alias for "ls -l", you should use a function, or an external shell script.

---

### Post by carn1x on 2010-12-19
> **gmargo said:**
> There's really no error to solve.  Bash aliases are quite limited and are essentially for substituting fixed strings.  In general, unless it's an alias for "ls -l", you should use a function, or an external shell script.

Ahh OK, thanks for the advice. Not sure why I seem invested in Aliases, I'll try to be more mindful of my selections in the future :)

---

