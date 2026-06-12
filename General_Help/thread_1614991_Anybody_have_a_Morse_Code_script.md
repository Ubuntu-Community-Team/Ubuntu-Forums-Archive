---
title: "Anybody have a Morse Code script?"
date: 2010-11-06
forum: General Help
---

### Post by inameiname on 2010-11-06
I'm looking for a simple Morse Code script that will convert any text (perhaps even .txt files) to Morse Code. I know there are plenty of Linux programs I could use, but I would like a simple script, whether it's perl, shell, bash, ruby, python, whatever. 

I've looked all over the net and can't seem to find one that works. Well, technically I found some that do seem to work, but only to convert Morse Code to text (and not well):

```

#Morse Code decoder - press ‘0&#8242; for dot, ‘1&#8242; for dash, and hit space (or enter) as a char separator
m=etianmsurwdkgohvf?l?pjbxcyzq;p=0;while read -sn1 c;do [ -z "$c" ]&&p=0&&echo&&continue;let p+=c;echo -ne \\b${m:$p:1};let p+=p+2;done

``````

#Morse decode using sed
#This is a short Morse code decoder written as a shellscript using sed.
#The Morse coded text should be in $text, and should be written with spaces between the letters.
echo $1\  | tr . 0 | sed -e {s/0----\ /1/g} -e {s/00---\ /2/g} -e {s/000--\ /3/g} -e {s/000-\ /4/g} -e {s/00000\ /5/g} -e {s/-0000\ /6/g} -e {s/--000\ /7/g} -e {s/---00\ /8/g} -e {s/----0\ /9/g} -e {s/-----\ /0/g} \
    | sed -e {s/-0-0\ /c/g} -e {s/-000\ /b/g} -e {s/00-0\ /f/g} -e {s/0000\ /h/g} -e {s/0---\ /j/g} -e {s/0-00\ /l/g} -e {s/0--0\ /p/g} -e {s/--0-\ /q/g} -e {s/000-\ /v/g} -e {s/-00-\ /x/g} -e {s/-0--\ /y/g} -e {s/--00\ /z/g} \
    | sed -e {s/0--\ /w/g} -e {s/-00\ /d/g} -e {s/--0\ /g/g} -e {s/-0-\ /k/g} -e {s/---\ /o/g} -e {s/0-0\ /r/g} -e {s/000\ /s/g} -e {s/00-\ /u/g} \
    | sed -e {s/0-\ /a/g} -e {s/00\ /i/g} -e {s/--\ /m/g} -e {s/-0\ /n/g} \
    | sed -e {s/0\ /e/g} -e {s/-\ /t/g}

```...and this one I think could work, but I don't know how to get it to work as I'm not big into python:

```

#!/usr/bin/env python

englishDict = {' ': ' ', '"': '.-..-.', "'": '.----.', '-': '-....-', ',': '--..--', '/': '-..-.', '.': '.-.-.-', '1': '.----', '0': '-----', '3': '...--', '2': '..---', '5': '.....', '4': '....-', '7': '--...', '6': '-....', '9': '----.', '8': '---..', ':': '---...', '?': '..--..', 'A': '.-', '@': '.--.-.', 'C': '-.-.', 'B': '-...', 'E': '.', 'D': '-..', 'G': '--.', 'F': '..-.', 'I': '..', 'H': '....', 'K': '-.-', 'J': '.---', 'M': '--', 'L': '.-..', 'O': '---', 'N': '-.', 'Q': '--.-', 'P': '.--.', 'S': '...', 'R': '.-.', 'U': '..-', 'T': '-', 'W': '.--', 'V': '...-', 'Y': '-.--', 'X': '-..-', 'Z': '--..'}
mcDict = dict([(x, y) for y, x in englishDict.iteritems()])

def toMC(english = 'hello, world'):
    english = english.upper()
    final = []
    for char in english:
        final.append(englishDict[char])
    return ' '.join(final)

def toEnglish(mc = '.... . .-.. .-.. --- --..--   .-- --- .-. .-.. -..'):
    word = mc.split('   ')
    mc = []
    for item in word:
        mc.append(item.split(' '))
    final = []
    for word in mc:
        for char in word:
            final.append(mcDict[char])
        final.append(' ')
    return ''.join(final)


##morse_code = """A .-
##B -...
##C -.-.
##D -..
##E .
##Z --..
##F ..-.
##G --.
##H ....
##I ..
##J .---
##K -.-
##L .-..
##M --
##N -.
##O ---
##P .--.
##Q --.-
##R .-.
##S ...
##T -
##U ..-
##V ...-
##W .--
##X -..-
##Y -.--
##Z --..
##0 -----
##1 .----
##2 ..---
##3 ...--
##4 ....-
##5 .....
##6 -....
##7 --...
##8 ---..
##9 ----.
##. .-.-.-
##, --..--
##? ..--..
##- -....-
##' .----.
##: ---...
##" .-..-.
##/ -..-.
##@ .--.-.
##    """
##morse_code = morse_code.split('\n')
##englishDict = {}
##for line in morse_code:
##    englishDict[line[0]] = line[2:]
##mcDict = dict([(x, y) for y, x in englishDict.iteritems()])
##l = []
##keys = englishDict.keys()
##for key in keys:
##    l.append((key, englishDict[key]))
##for item in l:
##    print str(item) + ',',

##Write a program that reads an English-language phrase and encodes the phrase into Morse code.
##Also,, the program should be able to read a phrase in Morse code and convert the phrase into
##the English-language equivalent. Use one blank between each Morse-coded letter and three blanks
##between each Morse-coded word.
##
##
##Example Input/Output
##CODE
##Morse: .... . .-.. .-.. ---   .-- --- .-. .-.. -..
##
##English: HELLO WORLD

##  International Morse Code
##A .-
##B -...
##C -.-.
##D -..
##E .
##Z --..
##F ..-.
##G --.
##H ....
##I ..
##J .---
##K -.-
##L .-..
##M --
##N -.
##O ---
##P .--.
##Q --.-
##R .-.
##S ...
##T -
##U ..-
##V ...-
##W .--
##X -..-
##Y -.--
##Z --..
##
##0 -----
##1 .----
##2 ..---
##3 ...--
##4 ....-
##5 .....
##6 -....
##7 --...
##8 ---..
##9 ----.
##
##Period .-.-.-
##Comma --..--
##? Mark ..--..
##Hyphen -....-
##Apostrophe .----.
##Colon ---...
##Quotation .-..-.
##Slash -..-.
##@ sign .--.-.

```

---

### Post by sohlinux on 2010-11-06
-.. .. -.. / -.-- --- ..- / - .-. -.-- / .--- .- ...- .- ..--.. 

[http://www.javascriptkit.com/script/script2/morse.shtml](http://www.javascriptkit.com/script/script2/morse.shtml)

---

### Post by ki4jgt on 2010-11-06
If you're wanting the beeps only you shouldn't need the char seperater. Just have the script insert a space after a given amount of time. If you use a space for a blank sound I fear you may get thrown off a lot! Just an idea.

Also if you want to learn CW (Morse Code) I've always been told that it is best not to learn it by ...---- as this meathod is very slow. It forces the user to translate from memory each character. It is best to learn from sound or rythm. Learning from rythm forces the brain to skip the translation part.

---

### Post by inameiname on 2010-11-06
Thanks for the link, but how would I go about making the into a script? Basically, so I can call the script, "./whatever.sh "text"", and have it convert it?

---

### Post by inameiname on 2010-11-06
I'm confused there. Do those scripts above give a signal output or something? Regardless, I have no idea how to tweak them, sorry. 

For now, I figured I'd find a simple script that would essentially, do this:

```

./script "SOS"
... --- ...

```

It'd be cool once having that if it'd have audio output besides the actual '.' and '-' characters, but I don't want to be too greedy, yet. :P

---

### Post by sohlinux on 2010-11-06
> **inameiname said:**
> Thanks for the link, but how would I go about making the into a script? Basically, so I can call the script, "./whatever.sh "text"", and have it convert it?

I would just execute it as java script with a JavaScript Shell

---

### Post by inameiname on 2010-11-06
Nah, I'm not doing this to learn it. I'd use one of those actual programs for that, as I know of many decent ones. I just want this as an easy reference tool, eventually throwing the equivalent of it in script form into a bash function so I can have it in my bash functions list and simple access from the terminal. Hope that helps my intent.

---

### Post by dino99 on 2010-11-06
there are some packages related to "morse" if you search it into synaptic

---

### Post by inameiname on 2010-11-06
I appreciate the info, but packages aren't what I am looking for. As I mentioned above, those packages in Synaptic are good for learning, and I would definitely use them if that was want I want, but I would like a simple conversion script, that's all. Much of the same way as I have scripts that convert to Roman Numerals, or convert to other languages.

---

### Post by dino99 on 2010-11-06
sorry i understand your frustation but you seem to be the only morse guru around, even a search on google dont give much solutions :(

---

### Post by inameiname on 2010-11-06
Hehe, no problem dino99. I appreciate the looking, though. Yeah, I couldn't find very much on a Morse Code converting script online. Guess most folks just prefer an actual GUI/application for such a thing, as those great applications found in Synaptic. But as noticed above with those I found, there is such a thing; they just go the one-way. :(

---

### Post by ki4jgt on 2010-11-06
I could write you one in BASIC really quickly, I'm not sure what all you want it to do, but you would have to use WINE to run it.

---

### Post by inameiname on 2010-11-06
Aww, that's quite nice of you, ki4jgt, but it probably wouldn't work well having to use Wine all the time. Plus, that'd make it hard to implement into a bash function, which I like to do for many of my scripts like I'd like this one to be.

---

### Post by ki4jgt on 2010-11-06
Correct me if I'm off:
You're wanting an sh file to output ../-- to the terminal and viceversa when you input ... you want s to come out.

Simply by running the command ./file.sh sos and the output would be .../---/...

---

### Post by inameiname on 2010-11-06
Yep, that's pretty much it.  It can be any type of script, ruby, python, perl, shell, bash, but the latter two are what I usually make so I'm used to making the most.

Basically, something simple where I can convert a word or phrase right from the command line.

And those first two scripts I gave above do just what I want, but only partially. If I write '...', it will output 's'. Just not the other way around.

---

### Post by sohlinux on 2010-11-06
how about this?

Input is ASCII text. Output can be: - . -..- - on the console

[http://sourceforge.net/projects/cwtext/](http://sourceforge.net/projects/cwtext/)

---

### Post by inameiname on 2010-11-06
I appreciate the find, but in script form it still doesn't quite seem to work. I actually found that very link a few hours ago, but after extracting 'gencw.py' from the tarball, it sadly didn't output what I wanted:

```

$ ./gencw.py "sos"
/* International Morse Code */
#define CWSTARTMASK (0x1f)
#define CWSIZEMASK (0x07)
#define CWSIZESHIFT (0x05)
char *crypt=".....-----....-.-.--..--..-...--.- ";
char *plain=".,:?-/=@!0123456789abcdefghijklmnopqrstuvwxyz";
char *code="\xcd\xd2\xc7\xd4\xc9\xb7\xad\xcb\xcb\xa5\xa4\xa3\xa2\xa1\xa0\xa9\xa8\xa7\xa6\x44\x89\x8e\x69\x20\x8c\x68\x80\x40\x84\x6e\x99\x45\x49\x65\x91\x9e\x6d\x60\x25\x63\x82\x64\x93\x90\x88";

```

For a second I was psyched, as I thought the line:

```

char *crypt=".....-----....-.-.--..--..-...--.- ";

```

But, that's obviously not "... --- ..."

Of course, maybe there's a way to make the whole tarball into a script, to work as I'd like. Way beyond me.

---

### Post by inameiname on 2010-11-06
Man, I wish this was in a script form, as that program (after actually installing it) does exactly what I'd like a script to do. It inputs and outputs just fine. Well, only ASCII text to Morse Code, not vice versa as well. Of course, those scripts above do that. Doh! Just want one simple that does both. hehe

---

### Post by sohlinux on 2010-11-06
> **inameiname said:**
> Man, I wish this was in a script form, as that program (after actually installing it) does exactly what I'd like a script to do. It inputs and outputs just fine. Well, only ASCII text to Morse Code, not vice versa as well. Of course, those scripts above do that. Doh! Just want one simple that does both. hehe

Im more of a radio ham than programmer but you could just reverse engineer cwtext so you can input -..- and output x

---

### Post by inameiname on 2010-11-06
I thought about that, but have no idea how, especially as what is made and installed are '.exe' files, not scripts. Besides, I wanted a simple script that'll do what I want, not a program to install. It's funny how I was able to find several Morse Code to Text scripts, which is perfect, but for one side of it, but yet, I have thus been unable to find a simple reverse script that does the same thing.

---

### Post by cipherboy_loc on 2010-11-06
I remember writing a Morse Code script in Perl... Let me dig it up and see if it works still. As for Bash, I have an idea.... Let me give it a go and I will let you now on the status of it. ;-)


Edit: I am working on a new version of the script. It needed a re-write.

Cipherboy

---

### Post by inameiname on 2010-11-06
Oh, awesome. Yeah, if you can find the Perl one, that'd be awesome. And of course, if the feeling moves you to try your hand in making a Bash one, I certainly wouldn't say no. ;) Thanks.

---

### Post by inameiname on 2010-11-06
This script does convert, but it converts to 1s and 0s, which represent dits and dahs and spaces in between:

```

#!/usr/bin/python

#short mark, dot or 'dit' (.) = 1
#longer mark, dash or 'dah' (-) = 111
#intra-character gap (between the dots and dashes within a character) = 0
#short gap (between letters) = 000
#medium gap (between words) = 0000000

import sys
__author__="Aanand Natarajan"

#morse code dictionary
codes = {'1':".----",'2':"..---",'3':"...--",'4':"....-",'5':".....",'6':"-....",'7':"--...",'8':"---..",
'9':"----.",'0':"-----",'A':".-",'B':"-...",'C':"-.-.",'D':"-..",'E':".",'F':"..-.",'G':"--.",
'H':"....",'I':"..",'J':".---",'K':"-.-",'L':".-..",'M':"--",'N':"-.",'O':"---",'P':".--.",
'Q':"--.-",'R':".-.",'S':"...",'T':"-",'U':"..-",'V':"...-",'W':".--",'X':"-..-",'Y':"-.--",
'Z':"--..",
#punctuations
',':"--..--",'.':".-.-.-",'?':"..--..",';':"-.-.-",':':"---...",'/':"-..-.",
'-':"-....-","'":".----.",'(':"-.--.",')':"-.--.-",'!':"-.-.--",'&':".-...",
'=':"-...-",'+':".-.-.",'_':"..--.-",'"':".-..-.",'$':"...-..-",'@':".--.-.",
#space
' ':"|"}

binary = {'.':'10','-':'1110',',':'000','|':'0000000'}


def encode(value):
    """ encodes the value into morse code """
    morse_value=""
    value.replace('*', 'X')
    value.replace('^', 'XX')
    for c in value:
       try :
               morse_value += codes[c.upper()]+','
       except :
         print "Unintended character " + c + " omitted"
    return _get_binary(morse_value)

def decode(morse_code_value):
    """ decodes the morse bytes """
    decoded_value = _decode_binary(morse_code_value)
    ascii_value=""
    for v in decoded_value.split(","):
        ascii_value += _get_key(v)
    return ascii_value

def _get_binary(value):
     binary_value = ""
     for c in value:
         binary_value += binary[c]
     return binary_value

def _get_key(value):
     """ returns the key for the given value """
     for k,v in codes.items():
         if v == value:
            return k
     return ''

def _decode_binary(binary):
    dah_replaced = binary.replace('1110', '-')
    dit_replaced = dah_replaced.replace('10', '.')
    comma_replaced = dit_replaced.replace('000', ',')
    zero_replaced = comma_replaced.replace('0', '|,')
    return zero_replaced

def _do_decode(value):
    print "Decoded : "+decode(value)

def _do_encode(value):
    print "Encoded : "+encode(value)

if __name__ == "__main__":
   if len(sys.argv) > 2:
      if sys.argv[1] == 'd' :
         print "decoding"
         _do_decode(sys.argv[2])
      else:
         print "encoding"
         _do_encode(sys.argv[2])
   elif len(sys.argv) > 1:
        print "encoding"
        _do_encode(sys.argv[1])
   else:
        print "Usage : "+sys.argv[0]+" [d (decode) |e (encode)] [input string]"

```

---

### Post by inameiname on 2010-11-06
I've changed the values a little bit of that python script, and it works just fine now. Of course, just for 'Text to Morse Code". Basically, I got the output to be the exact same as what is the output from the cwtext application that was mentioned as an alternative. So it does just what that one does now:

```

#!/usr/bin/python

#short mark, dot or 'dit' (.) = .
#longer mark, dash or 'dah' (-) = -
#intra-character gap (between the dots and dashes within a character) = no space
#short gap (between letters) = single space
#medium gap (between words) = double space

import sys
__author__="Aanand Natarajan"

#morse code dictionary
codes = {'1':".----",'2':"..---",'3':"...--",'4':"....-",'5':".....",'6':"-....",'7':"--...",'8':"---..",
'9':"----.",'0':"-----",'A':".-",'B':"-...",'C':"-.-.",'D':"-..",'E':".",'F':"..-.",'G':"--.",
'H':"....",'I':"..",'J':".---",'K':"-.-",'L':".-..",'M':"--",'N':"-.",'O':"---",'P':".--.",
'Q':"--.-",'R':".-.",'S':"...",'T':"-",'U':"..-",'V':"...-",'W':".--",'X':"-..-",'Y':"-.--",
'Z':"--..",
#punctuations
',':"--..--",'.':".-.-.-",'?':"..--..",';':"-.-.-",':':"---...",'/':"-..-.",
'-':"-....-","'":".----.",'(':"-.--.",')':"-.--.-",'!':"-.-.--",'&':".-...",
'=':"-...-",'+':".-.-.",'_':"..--.-",'"':".-..-.",'$':"...-..-",'@':".--.-.",
#space
' ':"|"}

binary = {'.':'.','-':'-',',':' ','|':'  '}


def encode(value):
    """ encodes the value into morse code """
    morse_value=""
    value.replace('*', 'X')
    value.replace('^', 'XX')
    for c in value:
       try :
               morse_value += codes[c.upper()]+','
       except :
         print "Unintended character " + c + " omitted"
    return _get_binary(morse_value)

def decode(morse_code_value):
    """ decodes the morse bytes """
    decoded_value = _decode_binary(morse_code_value)
    ascii_value=""
    for v in decoded_value.split(","):
        ascii_value += _get_key(v)
    return ascii_value

def _get_binary(value):
     binary_value = ""
     for c in value:
         binary_value += binary[c]
     return binary_value

def _get_key(value):
     """ returns the key for the given value """
     for k,v in codes.items():
         if v == value:
            return k
     return ''

def _decode_binary(binary):
    dah_replaced = binary.replace('-', '-')
    dit_replaced = dah_replaced.replace('.', '.')
    comma_replaced = dit_replaced.replace(' ', ',')
    zero_replaced = comma_replaced.replace('', '|,')
    return zero_replaced

def _do_decode(value):
    print "Decoded : "+decode(value)

def _do_encode(value):
    print "Encoded : "+encode(value)

if __name__ == "__main__":
   if len(sys.argv) > 2:
      if sys.argv[1] == 'd' :
         print "decoding"
         _do_decode(sys.argv[2])
      else:
         print "encoding"
         _do_encode(sys.argv[2])
   elif len(sys.argv) > 1:
        print "encoding"
        _do_encode(sys.argv[1])
   else:
        print "Usage : "+sys.argv[0]+" [d (decode) |e (encode)] [input string]"

```And so technically, along with that one above, I can use the first script I mentioned in this thread for the reversal, and I got what I want:

```

#!/bin/bash

#this is a short Morse code decoder written as a shellscript using sed
#the Morse coded text should be written with spaces between the letters
#only good to convert from Morse code to text
#by scvalex

echo $1\  | tr . 0 | sed -e {s/0----\ /1/g} -e {s/00---\ /2/g} -e {s/000--\ /3/g} -e {s/000-\ /4/g} -e {s/00000\ /5/g} -e {s/-0000\ /6/g} -e {s/--000\ /7/g} -e {s/---00\ /8/g} -e {s/----0\ /9/g} -e {s/-----\ /0/g} \
    | sed -e {s/-0-0\ /c/g} -e {s/-000\ /b/g} -e {s/00-0\ /f/g} -e {s/0000\ /h/g} -e {s/0---\ /j/g} -e {s/0-00\ /l/g} -e {s/0--0\ /p/g} -e {s/--0-\ /q/g} -e {s/000-\ /v/g} -e {s/-00-\ /x/g} -e {s/-0--\ /y/g} -e {s/--00\ /z/g} \
    | sed -e {s/0--\ /w/g} -e {s/-00\ /d/g} -e {s/--0\ /g/g} -e {s/-0-\ /k/g} -e {s/---\ /o/g} -e {s/0-0\ /r/g} -e {s/000\ /s/g} -e {s/00-\ /u/g} \
    | sed -e {s/0-\ /a/g} -e {s/00\ /i/g} -e {s/--\ /m/g} -e {s/-0\ /n/g} \
    | sed -e {s/0\ /e/g} -e {s/-\ /t/g}

```Of course, having to use two scripts kind of sucks, and they are exactly pretty. So I am definitely interested in yours...or anyone elses.

Finally, here is my bash functions....like I said, they work, though, the 'morse2text' function/script generates the whole words as one long word. It'd be nice to have spaces, but that's not a big issue:

```

##################################################
# Morse code encoding and decoding               #
##################################################

#this is a short Morse code decoder written as a shellscript using sed
#the Morse coded text should be written with spaces between the letters
#only good to convert from Morse code to text
#by scvalex
function morse2text()
{
echo $1\  | tr . 0 | sed -e {s/0----\ /1/g} -e {s/00---\ /2/g} -e {s/000--\ /3/g} -e {s/000-\ /4/g} -e {s/00000\ /5/g} -e {s/-0000\ /6/g} -e {s/--000\ /7/g} -e {s/---00\ /8/g} -e {s/----0\ /9/g} -e {s/-----\ /0/g} \
    | sed -e {s/-0-0\ /c/g} -e {s/-000\ /b/g} -e {s/00-0\ /f/g} -e {s/0000\ /h/g} -e {s/0---\ /j/g} -e {s/0-00\ /l/g} -e {s/0--0\ /p/g} -e {s/--0-\ /q/g} -e {s/000-\ /v/g} -e {s/-00-\ /x/g} -e {s/-0--\ /y/g} -e {s/--00\ /z/g} \
    | sed -e {s/0--\ /w/g} -e {s/-00\ /d/g} -e {s/--0\ /g/g} -e {s/-0-\ /k/g} -e {s/---\ /o/g} -e {s/0-0\ /r/g} -e {s/000\ /s/g} -e {s/00-\ /u/g} \
    | sed -e {s/0-\ /a/g} -e {s/00\ /i/g} -e {s/--\ /m/g} -e {s/-0\ /n/g} \
    | sed -e {s/0\ /e/g} -e {s/-\ /t/g}
}



function text2morse()
{
cat > "/tmp/text2morse.py" <<"End-of-message"
#!/usr/bin/python
#short mark, dot or 'dit' (.) = .
#longer mark, dash or 'dah' (-) = -
#intra-character gap (between the dots and dashes within a character) = no space
#short gap (between letters) = single space
#medium gap (between words) = double space
import sys
__author__="Aanand Natarajan"
#morse code dictionary
codes = {'1':".----",'2':"..---",'3':"...--",'4':"....-",'5':".....",'6':"-....",'7':"--...",'8':"---..",
'9':"----.",'0':"-----",'A':".-",'B':"-...",'C':"-.-.",'D':"-..",'E':".",'F':"..-.",'G':"--.",
'H':"....",'I':"..",'J':".---",'K':"-.-",'L':".-..",'M':"--",'N':"-.",'O':"---",'P':".--.",
'Q':"--.-",'R':".-.",'S':"...",'T':"-",'U':"..-",'V':"...-",'W':".--",'X':"-..-",'Y':"-.--",
'Z':"--..",
#punctuations
',':"--..--",'.':".-.-.-",'?':"..--..",';':"-.-.-",':':"---...",'/':"-..-.",
'-':"-....-","'":".----.",'(':"-.--.",')':"-.--.-",'!':"-.-.--",'&':".-...",
'=':"-...-",'+':".-.-.",'_':"..--.-",'"':".-..-.",'$':"...-..-",'@':".--.-.",
#space
' ':"|"}
binary = {'.':'.','-':'-',',':' ','|':'  '}
def encode(value):
    """ encodes the value into morse code """
    morse_value=""
    value.replace('*', 'X')
    value.replace('^', 'XX')
    for c in value:
       try :
               morse_value += codes[c.upper()]+','
       except :
         print "Unintended character " + c + " omitted"
    return _get_binary(morse_value)
def decode(morse_code_value):
    """ decodes the morse bytes """
    decoded_value = _decode_binary(morse_code_value)
    ascii_value=""
    for v in decoded_value.split(","):
        ascii_value += _get_key(v)
    return ascii_value
def _get_binary(value):
     binary_value = ""
     for c in value:
         binary_value += binary[c]
     return binary_value
def _get_key(value):
     """ returns the key for the given value """
     for k,v in codes.items():
         if v == value:
            return k
     return ''
def _decode_binary(binary):
    dah_replaced = binary.replace('-', '-')
    dit_replaced = dah_replaced.replace('.', '.')
    comma_replaced = dit_replaced.replace(' ', ',')
    zero_replaced = comma_replaced.replace('', '|,')
    return zero_replaced
def _do_decode(value):
    print "Decoded : "+decode(value)
def _do_encode(value):
    print "Encoded : "+encode(value)
if __name__ == "__main__":
   if len(sys.argv) > 2:
      if sys.argv[1] == 'd' :
         print "decoding"
         _do_decode(sys.argv[2])
      else:
         print "encoding"
         _do_encode(sys.argv[2])
   elif len(sys.argv) > 1:
        print "encoding"
        _do_encode(sys.argv[1])
   else:
        print "Usage : "+sys.argv[0]+" [d (decode) |e (encode)] [input string]"
End-of-message
chmod +x "/tmp/text2morse.py"
"/tmp/text2morse.py" "$1"
rm "/tmp/text2morse.py"
}

```Again, a better one is more than welcome. Nonetheless, I'll still mark this as solved.

---

### Post by Jforce93 on 2010-11-06
I'll see what i can do. Is python good?

---

### Post by inameiname on 2010-11-06
Oh cool. Just do whatever format you'd like.

---

### Post by cipherboy_loc on 2010-11-07
Almost done. I just need to comment my work, and I will post it. While reading --help is good, the best way to find out all the arguments (or all variations on the ones described in --help) is to read the source code. I made sure to comment what I was doing.


PM me with any questions about the script.

Cipherboy_LOC

---

### Post by cipherboy_loc on 2010-11-07
I attached the source. The old code really needed a re-write, so I did that.

Morse Code Converter version 2
Copyright (C) 2010 Cipherboy_LOC
Licensed under the GNU General Public License version 3.

Attached as a tar ball. Written in Perl, no dependencies except a valid Perl interpretor (Though it uses strict so it should be available on a wider-range of interpretors). 

SHA512 sum:

180b7d0cb080782bacbb4785bbdccfb9d540d847ee77255940d4c04b566f8f6186a0712c44077f20e0db85d5b84008e61c4c2dd95a3ce01758c9299260111892  ./MorseCodeV2.tar.gz

MD5 sum
e7fabe6e9cc82fa6ff29beb4fa510f12  ./MorseCodeV2.tar.gz


Cipherboy.

---

### Post by WG- on 2010-11-07
Interesting thread.

---

### Post by inameiname on 2010-11-08
Cool. Thanks for all the hard work. However, the tarball won't extract. It gives me this error, so I can't do anything yet:

```

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error is not recoverable: exiting now

```

UPDATE:

Hey, I got it extracted. For some reason the normal "extract here" didn't work like I would normally with tarballs. I had to install 'bsdtar', and then it opened it just fine. Very strange.

---

### Post by sohlinux on 2010-11-08
nice program :P

---

### Post by inameiname on 2010-11-08
Thank you. It works just like those two I posted above, but much, much neater and cleaner. Thanks.

Oh, there is one thing to note though. When encrypting either text or a file into morse code, it works just fine, but when trying to decrypt morse code file that's already been encrypted, it won't decrypt it neither in the terminal, or if I try to just output it into a file.

```

$ ./morsecode2.pl -e -t "hello, how are you doing, today....don't forget the roses"
.... . .-.. .-.. --- ..-..   .... --- .--   .- .-. .   -.-- --- ..-   -.. --- .. -. --. ..-..   - --- -.. .- -.-- .-.-.- .-.-.- .-.-.- .-.-.- -.. --- -. .----. -   ..-. --- .-. --. . -   - .... .   .-. --- ... . ...  
$ ./morsecode2.pl -e -t "hello, how are you doing, today....don't forget the roses" -o test_encrypted.txt
$ ./morsecode2.pl -d -t ".... . .-.. .-.. --- ..-..   .... --- .--   .- .-. .   -.-- --- ..-   -.. --- .. -. --. ..-..   - --- -.. .- -.-- .-.-.- .-.-.- .-.-.- .-.-.- -.. --- -. .----. -   ..-. --- .-. --. . -   - .... .   .-. --- ... . ... "
hello,howareyoudoing,today....don'tforgettheroses
$ ./morsecode2.pl -d -i test_encrypted.txt

$ ./morsecode2.pl -d -i test_encrypted.txt -o test_originaltext.txt


```Also, not to be super greedy, is there a way to have it decrypted with spaces in between the words, so instead of the above's: hello,howareyoudoing,today....don'tforgettheroses, it is hello, how are you doing, today....don't forget the roses?

Also, another little thing I found in your script:

```

$ ./morsecode2.pl -e -s
What would you like to encrypt in Morse Code?
> are us
.- .-. .   ..- ...  
$ ./morsecode2.pl -d -s
What would you like to encrypt in Morse Code?            <---------should be decrypt
> .- .-. .   ..- ... 
areus

$ ./morsecode2.pl -e -s
What would you like to encrypt/decrypt in Morse Code?
> are us
.- .-. .   ..- ...  
$ ./morsecode2.pl -d -s
What would you like to encrypt/decrypt in Morse Code?    <---------so I changed it to encrypt/decrypt
> .- .-. .   ..- ... 
areus

So I just changed line 251 from 'encrypt' to 'encrypt/decrypt'. No biggie.

```

Also, on some text files that I have when I encrypt whatever to a text file, the resultant text file output, generates this, over and over:

```

$ ./morsecode2.pl -d -i "-. --- -. -....- - . -..- - .. -. .--. ..-"
No such file or directory -. --- -. -....- - . -..- - .. -. .--. ..-...
$ 

..."No such file or directory" and then some morse code over and over....

```

---

### Post by inameiname on 2010-11-08
I'm also curious about having it read the encrypted morse code if a '-t' output is desired. That would be cool as another option. I'll look into it and see if I can.

---

### Post by cipherboy_loc on 2010-11-08
I fixed the previous issues (Including the -d -s options one), but I don't understand what you want with this:
> **inameiname said:**
> I'm also curious about having it read the encrypted morse code if a '-t' output is desired. That would be cool as another option. I'll look into it and see if I can.


Please explain. Also, I could not replicate your last bug,
> 
Code:
$ ./morsecode2.pl -d -i "-. --- -. -....- - . -..- - .. -. .--. ..-"
No such file or directory -. --- -. -....- - . -..- - .. -. .--. ..-...
$ 

..."No such file or directory" and then some morse code over and over....I don't get that last line > ..."No such file or directory" and them some morse code over and over....
I don't know if this is what you mean, but I get this:

```

cipherboy@cipherboy-workstation:~/Desktop/Perl/M/tmp$ ./morsecode2.pl -d -i "-. --- -. -....- - . -..- - .. -. .--. ..-"
No such file or directory -. --- -. -....- - . -..- - .. -. .--. ..-...
cipherboy@cipherboy-workstation:~/Desktop/Perl/M/tmp$ 

```



Edit: Whoops, forgot to attach the files... See next post.

---

### Post by cipherboy_loc on 2010-11-08
Attached.

---

### Post by inameiname on 2010-11-09
Sorry if I didn't explain myself super well...let me see...

As far as the reading of the encrypted stuff, I was just thinking about another cool option that could exist where not only would it encrypt from text to morse code, it could even give you audio readout of it, with beeps or whatnot. Just something cool I thought might really add to such amazing work you've already done. When I have more time, I'll look more into such myself. Shame a simple 'espeak' command fails to read '.' and '-' 's. 

Finally, as for my "No such file or directory..." error, from the one you have been able to generate, it seems the same as mine. I just noticed sometimes after I unsuccessfully converted back a text file of encrypted text that was made with "./morsecode2.pl -e -t "sfdsfdsfdfdfdfdfdf" -o whatever.txt", which I then just copied and pasted a section of what was outputed in "whatever.txt", (not with the '-i' but with '-t' since here I won't be using the "whatever.txt" but just a copied and pasted part of it), "./morsecode2.pl -d -t "whatevermorsecodehere", it popped up that error. Perhaps, now that you mentioned you fixed the output to text file and decrypt back issue, it might have fixed that issue, Idk.

Anyway, I'll check out the new versions. Thank you.


UPDATE:

Awesome, seems as though all has been fixed. Cool. Thanks, heaps.


I am curious if this is also possible. I've never seen it in any morse code encryption/decryption I've ever seen before, so I doubt it's possible, but here goes: Is is possible to have it encrypt an entire file, and leave it at the format it's in, as in it includes where a text file as indention, paragraphs, line breaks, whatever? Basically, if you've ever encrypted/decrypted a text file through Linux, the text file is 'coded' in whatever format you set as your parameters, but then when you 'decode' it, it generates the exact text file that you had before, indention, paragraphs, capitalization, and everything as it was before. Just makes me curious of that's possible with a morse code encryption/decryption. Of course, don't bother if you think it'd be too much of a question possible, as you've definitely done way more than you needed to help me with my little thread on here.

---

### Post by cipherboy_loc on 2010-11-09
I have not added it yet, but if you convert . to dit and - to dah you can use espeak:

```
cipherboy@cipherboy-workstation:~$ espeak "dit dit dit         dah dah dah     dit dit dit"
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
cipherboy@cipherboy-workstation:~$ 
```

From [http://en.wikipedia.org/wiki/Morse_code#Development_and_history:](http://en.wikipedia.org/wiki/Morse_code#Development_and_history:)
> []("http://en.wikipedia.org/wiki/Morse_code#cite_note-2") To reflect the sounds of Morse code receivers, the operators began to  vocalise a dot as "dit", and a dash as "dah". Dots which are not the  final element of a character became vocalised as "di". For example, the  letter "c" was then vocalised as "dah-di-dah-dit".[[4]]("http://en.wikipedia.org/wiki/Morse_code#cite_note-3")[[5]]("http://en.wikipedia.org/wiki/Morse_code#cite_note-4")


I will probably use this library [http://search.cpan.org/dist/Speech-eSpeak/lib/Speech/eSpeak.pm](http://search.cpan.org/dist/Speech-eSpeak/lib/Speech/eSpeak.pm) for the espeak integration...

---

### Post by inameiname on 2010-11-09
Yeah, that's the method I was thinking about just doing, changing it to 'dah''s and 'dit''s for espeak to handle. I did that for the 'encrypt' version I had found way above. That'd be awesome if you have that as another option in yours, though. I was also thinking about how to make actual 'dot' computer beeps and 'long dot' noises too, but haven't figured that out yet as that would sound just like actual morse code.

You should post your perl script on 'www.gnome-look.org' or something, for others to benefit from it. There are many of my fellow geeks out there, especially on that site, who love these sort of things. ;)

---

### Post by cipherboy_loc on 2010-11-09
I am working on creating a deb package to post on launchpad. I think the link is:
[https://launchpad.net/~cipherboy-loc/+archive/perl-morsecode](https://launchpad.net/~cipherboy-loc/+archive/perl-morsecode)

To add:
```
sudo apt-add-repository ppa:cipherboy-loc/perl-morsecode


```


Note: there are no packages uploaded yet.





Cipherboy

---

### Post by inameiname on 2010-11-09
Neato. So how would it work?....Once installed, you can just type 'morse' or something and it'll pop up the script's stuff in much of the same way as './morsecode2.pl'?

---

### Post by cipherboy_loc on 2010-11-09
Hm.. Its not going up..  I created a .deb package, but it won't go up here: [https://launchpad.net/perl-morsecode-v2](https://launchpad.net/perl-morsecode-v2)

Is there a good tutorial for how to create and upload .deb packages to a launchpad repository?

Cipherboy

---

### Post by inameiname on 2010-11-09
Yeah, I've had issues myself with trying to upload stuff. Here are the basic steps, in my own words:

```

(for source tar file, the right way) (needs: sudo apt-get install build-essential autoconf automake autotools-dev dh-make debhelper devscripts dput fakeroot xutils lintian pbuilder):

    1. gpg --gen-key # only needed if adding to PPAs and/or to official repos
    2. tar xvf sourcefilesarchive.tar.gz
    3. cd /path/to/extracted/sourcefiles
    4. dh_make -n -s -e your@emailaddress.com
    5. dpkg-depcheck -d ./configure    # find dependencies, and once found, add to section in subdirectory DEBIAN/control in the package directory
    6. Edit changelog, copyright, control, rules, manpage (if want to adhere to policy, ensure name & email are = what's on record for your gpp key)
    7. fakeroot debian/rules clean && fakeroot debian/rules binary
           dpkg-buildpackage -rfakeroot    # requires signature and a .changes file (needed for adding to PPAs)
       dpkg-buildpackage -rfakeroot -us -uc    # does not require signature and a .changes files
    8. lintian -Ivi ../yourpackage.changes    # optional, to check the new deb package
    9. dput ppa:<yourppausername>/l<yourppaname> <package.changes>    # optional, to upload to a Launchpad PPA

```...And here is a good link to a nice, and more detailed plan to build and upload to Launchpad:

[http://www.webupd8.org/2010/01/how-to-create-deb-package-ubuntu-debian.html](http://www.webupd8.org/2010/01/how-to-create-deb-package-ubuntu-debian.html)

---

### Post by cipherboy_loc on 2010-11-09
So I have the Debian package build (using a slightly different method: I modified an existing package to suite my needs (took it apart, rebuilt it)) and it works. How do I post it on Launchpad without needing a .changes file?




Cipherboy

---

### Post by inameiname on 2010-11-10
I'm afraid you must have a '.changes' file. Plus, you cannot upload packages already in deb form on Launchpad. It's sucks, I know. I have several I just make from scratch, but because they aren't 'official Launchpad created debs', I can't put in a PPA of my own. :( Anyway, here explains this:

[https://help.launchpad.net/Packaging](https://help.launchpad.net/Packaging)
and
[https://help.launchpad.net/Packaging/PPA/Uploading](https://help.launchpad.net/Packaging/PPA/Uploading)

---

### Post by cipherboy_loc on 2010-11-10
Okay, so it tells me (on my launchpad page) to upload stuff via:

```
dput ppa:cipherboy-loc/perl-morsecode <source.changes>
```


So I run it like this (-P for passive mode, -U so as to save my self from having to delete .ppa.upload every time, and -u to skip the GPG verification (which is missing...)):
```
cipherboy@cipherboy-workstation:~/build$ dput -u -P -U ppa:cipherboy-loc/perl-morsecode  ./mc2_2.0.1_i386.changes
Uploading to ppa (via ftp to ppa.launchpad.net):
  Uploading mc2_2.0.1.dsc: done.
  Uploading mc2_2.0.1.tar.gz: done.  
  Uploading mc2_2.0.1_i386.deb: done.
  Uploading mc2_2.0.1_i386.changes: done.
Successfully uploaded packages.
cipherboy@cipherboy-workstation:~/build$ 

```

But it says om my repository that it is not there.... Any ideas?




Thanks,
Cipherboy

---

### Post by inameiname on 2010-11-10
I'm afraid I'm probably not the best person to ask as I've never been able to successfully upload anything to Launchpad. I can get it to where it seems as though it was successful, even says all went well, but when I go into my PPA, nothing ever shows up. Not sure why.

Anyway, you mentioned the '-u- option said the .gpg key was missing or something...you have to have that to be able to upload anything. You have to get one for your computer, and your launchpad account before you can ever upload anything. Such a hastle, isn't it?

---

### Post by cipherboy_loc on 2010-11-10
I signed all the files that got uploaded, changed the md5, sha1, and sha256 sums in the .changes file, then ran dput and got the following output:

```

cipherboy@cipherboy-workstation:~/build$ dput ppa:cipherboy-loc/perl-morsecode  ./mc2_2.0.1_i386.changes
Checking signature on .changes
gpg: Signature made Wed 10 Nov 2010 05:00:58 PM CST using RSA key ID 50643956
gpg: Good signature from "Alex Scheel (Launchpad ID GPG key) <xxxxxxxxxxxxxxxx@XXXXXXXXXXXXXXX.com>"
Good signature on ./mc2_2.0.1_i386.changes.
Checking signature on .dsc
gpg: Signature made Wed 10 Nov 2010 04:52:59 PM CST using RSA key ID 50643956
gpg: Good signature from "Alex Scheel (Launchpad ID GPG key) <xxxxxxxxxxxxxxxx@XXXXXXXXXXXXXXX.com>"
Good signature on ./mc2_2.0.1.dsc.
size doesn't match for ./mc2_2.0.1.dsc
size doesn't match for ./mc2_2.0.1.tar.gzLaunchpad failed to process the upload path '~perl-morsecode-v2/ubuntu':
size doesn't match for ./mc2_2.0.1_i386.deb
Uploading to ppa (via ftp to ppa.launchpad.net):
  Uploading mc2_2.0.1.dsc: done.
  Uploading mc2_2.0.1.tar.gz: done.  
  Uploading mc2_2.0.1_i386.deb: done.
  Uploading mc2_2.0.1_i386.changes: done.
Successfully uploaded packages.

```I am going to wait 10 minutes to see if it has uploaded... If not, I will submit defeat. I doubt they could make it any harder.... ;-)


Well, I have waited, and I realized I got an email saying it could not find the "stable" branch... Oh well. Guess I will just create my own thread and post my updates to the Morse Code V2 program...





Cipherboy

---

### Post by inameiname on 2010-11-11
Sorry it's not working for ya. That's the messages I got to whenever I've tried to upload stuff to a PPA on Launchpad. Not sure why they never go through, even though it says they were successful. I've tried small and large packages, and none work. 

As you said, they couldn't make it any more difficult. :P I think it's funny how so many folks are wary of using PPAs because of untrusted sources, yet I'm sure most don't get just how hard it is to put anything on them in the first place! Why bother if you are gonna put up bad software for us. hehe

---

