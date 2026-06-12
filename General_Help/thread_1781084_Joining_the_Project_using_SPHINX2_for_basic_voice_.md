---
title: "Joining the Project using SPHINX2 for basic voice commands with USB mic"
date: 2011-06-12
forum: General Help
---

### Post by honeybear on 2011-06-12
Hi,

**How to compare two wav files [http://www.perlmonks.org/?node_id=169641](http://www.perlmonks.org/?node_id=169641) or to be capable to reco simple voice commands?**

Openbox, fluxbox, ... can be ran using perlbox voice reco for basic commands. Here please find an howto: 
[http://knoppmyth.net/phpBB2/viewtopic.php?p=110384&sid=0d0495792032e37715560a9269f12c06](http://knoppmyth.net/phpBB2/viewtopic.php?p=110384&sid=0d0495792032e37715560a9269f12c06)

eVERY THING IS FREQUENCE BASED: [http://www-rohan.sdsu.edu/~ling354/jackspra.jpg](http://www-rohan.sdsu.edu/~ling354/jackspra.jpg)

However we would like to make the use of the ALSA and processing after recording. OK. 

```
apt-get install -f sphinx2
```


here is my script, please improve it:

```

#!/bin/sh
# my alsa-1 is my usb mic
arecord -Dplughw:1,0 -f cd -vv voicecommand.wav
sphinx2-continuous -live TRUE -ctloffset 0 -ctlcount 100000000 -cepdir /usr/share/sphinx2/model/lm/turtle/ctl -datadir /usr/share/sphinx2/model/lm/turtle/ctl -agcemax TRUE -langwt 6.5 -fwdflatlw 8.5 -rescorelw 9.5 -ugwt 0.5 -fillpen 1e-10 -silpen 0.005 -inspen 0.65 -top 1 -topsenfrm 3 -topsenthresh -70000 -beam 2e-06 -npbeam 2e-06 -lpbeam 2e-05 -lponlybeam 0.0005 -nwbeam 0.0005 -fwdflat FALSE -fwdflatbeam 1e-08 -fwdflatnwbeam 0.0003 -bestpath TRUE -kbdumpdir /usr/share/sphinx2 -lmfn /usr/share/sphinx2/model/lm/turtle/turtle.lm -dictfn /usr/share/sphinx2/model/lm/turtle/turtle.dic -ndictfn /usr/share/sphinx2/model/hmm/6k/noisedict -phnfn /usr/share/sphinx2/model/hmm/6k/phone -mapfn /usr/share/sphinx2/model/hmm/6k/map -hmmdir /usr/share/sphinx2/model/hmm/6k -hmmdirlist /usr/share/sphinx2/model/hmm/6k -8bsen TRUE -sendumpfn /usr/share/sphinx2/model/hmm/6k/sendump -cbdir /usr/share/sphinx2/model/hmm/6k   < voicecommand.wav  # export to .thetextfile

VOICECOMMAND=`cat .thetextfile`
if [ "$VOICECOMMAND" = "firefox" ]  ; then 
     firefox 
fi

if [ "$VOICECOMMAND" = "xterm" ]  ; then 
     xterm 
fi



```

THe next step is to analyses the wav file just created.

The advantage is that sphinx2 works for basic commands + it uses only up to 3% of your CPU ressources !!

Enjoy




-- 
Sphinx2 manual : [http://www.cs.cmu.edu/~archan/s_info/Sphinx2/sphinx2.html](http://www.cs.cmu.edu/~archan/s_info/Sphinx2/sphinx2.html)

---

### Post by honeybear on 2011-06-12
About an hour or two later he had Sphinx working by passing the client script a .wav file and it would return the correct text. 


Here I could find someone that already use it as like that for other application:

[http://www.latinsud.com/pub/asterisk-sphinx/asterisk-sphinx.html](http://www.latinsud.com/pub/asterisk-sphinx/asterisk-sphinx.html)

/usr/local/bin/decoder2
```


#!/bin/sh
BASE=6403
S2BATCH=sphinx2-continuous
HMM=/usr/local/share/sphinx2/model/hmm/6k
TASK=/usr/local/share/sphinx2/model/lm/${BASE}
CTLFILE=/usr/local/share/sphinx2/model/lm/${BASE}/${BASE}.ctl
#BASE=$1
$S2BATCH -nbest 1 -nbestdir /tmp -verbose 0 -adcin TRUE -adcext wav -ctlfn 
${CTLFILE} -ctloffset 0 -ctlcount 100000000 -datadir ${TASK} -samp 8000 
-agcmax TRUE -langwt 6.5 -fwdflatlw 8.5 -rescorelw 9.5 -ugwt 0.5 -fillpen 
1e-10 -silpen 0.005 -inspen 0.65 -top 1 -topsenfrm 3 -topsenthresh -70000 
-beam 2e-06 -npbeam 2e-06 -lpbeam 2e-05 -lponlybeam 0.0005 -nwbeam 0.0005 
-fwdflat FALSE -fwdflatbeam 1e-08 -fwdflatnwbeam 0.0003 -bestpath TRUE 
-kbdumpdir ${TASK} -lmfn ${TASK}/${BASE}.lm -dictfn ${TASK}/${BASE}.dic 
-noisedict ${HMM}/noisedict -phnfn ${HMM}/phone -mapfn ${HMM}/map -hmmdir 
${HMM} -hmmdirlist ${HMM} -8bsen TRUE -sendumpfn ${HMM}/sendump -cbdir ${HMM}


My php-test.agi:

function __write__($line)
{
        print $line."\n";
}

function __read__()
{
        global $in;
        $input=str_replace("\n","",fgets($in,4096));
        return $input;
}

function festival($texto)
{
        __write__("EXEC FESTIVAL \"$texto\"");
        return __read__();
}

function record($filename, $digits)
{
        __write__("RECORD FILE $filename wav $digits 15000 BEEP");
        return __read__();
}

$in=fopen("php://stdin","r");
festival("ingrese su mensaje");
record("mensaje","#");
$comando="/usr/local/bin/decoder2";                
$value=file("/tmp/mensaje.hyp");
$value=$value[0];
$numero=trim(substr($value,strpos($value,">")+1));
if($numero!="")
	festival("usted a seleccionado el numero $numero");
exec($comando);



```

it is interesting



[http://www.syednetworks.com/asterisk-integration-with-sphinx-voice-recognition-system](http://www.syednetworks.com/asterisk-integration-with-sphinx-voice-recognition-system)


Speech reco for asterisk : [http://forum.linuxmce.org/index.php?topic=189.0;wap2](http://forum.linuxmce.org/index.php?topic=189.0;wap2)

---

### Post by manzdagratiano on 2011-06-13
This looks awesome!!! I will soon give it a shot!

---

### Post by honeybear on 2011-06-13
> **manzdagratiano said:**
> This looks awesome!!! I will soon give it a shot!

Well it is not working... the problem is how to run the batch on a wav file so that sphinx2 can detect words

the sphinx2 is much accurate with USB microphone which are of higher quality

---

