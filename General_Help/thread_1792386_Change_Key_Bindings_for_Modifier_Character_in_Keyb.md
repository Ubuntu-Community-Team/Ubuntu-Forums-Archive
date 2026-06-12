---
title: "Change Key Bindings for Modifier Character in Keyboard layout"
date: 2011-06-28
forum: General Help
---

### Post by ellaivarios on 2011-06-28
**xmodmap -- Change unicode Key Bindings for dead_acute into another dead_acute unicode binding**


I do not have this problem in MS Windows!!! Grrr)
 
I use **Ubuntu 10.04**, **Openoffice 3.02** and I need to be able to write correctly in **Ancient Greek**. My keyboard layout model is set to **Dell PrecisionM65**  (I have a Dell Inspiron 9400 laptop, but Dell PrecisionM65 from  the list is the exact match for my keyboard -- my exact model does not appear, all other keyboards do not  look right or respond 100% or match my keyboard layout 100%). I have two keyboard layouts: **USA** and **Greece Polytonic**. I switch between keyboard layouts using Ctrl+Shift, in case it matters.

Recently, I downloaded this awesome Ancient Greek Spellchecker, which  takes care of much hassle in mistakes concerning diacritics (diacritics  are little symbols on top of vowels, such as what you would commonly  know as: acute accent, acute grave, etc, also known to us classicists as  daseia, psili, oxia, baria, perispomene, upogegrammene, dialytika,  etc.). 

However, I noticed that the diacritic associated with the Oxia (the  acute accent -- it looks like a tiny frontslash but on top of a vowel)  that my computer outputs, is not correct, which also results in the  spell checker "seeing" words that are spelled correctly as incorrect. On  a closer inspection one notices that what is supposed to be outputed as  an Oxia is not bound to the keys it is supposed to, but my computer  outputs a Tonos instead (this is happening on almost every single Linux  xomputer I have gotten my hands on since i discovered this problem and  asked friends). This difference goes far beyond the simple  issue of making the typing of words "appear" correct, or be suitable for  the spellchecker, whose settings are correct by the way. It is a matter  of setting the Operating System to output key bindings correctly, and  it also matters for educational reasons, when typing serious texts,  because the Tonos and the Oxia may look similar, but they are not the  same.

In ancient Greek, the Oxia is used to signify high pitch in  the pronunciation of a word. In modern Greek, the Tonos is used to  signify stress in the pronunciation of a word. The difference between  the two is also in writing: the oxeia is literally like a tiny  frontslash over the vowel, while the Tonos is like an almost vertical  line over the vowel. This must be corrected. For some reason when I type  an Oxia using the Greek Polytonic keyboard layout, I get a Tonos. It is  either that the keys are incorrectly bound, or that it overrides it  somehow.

For your visual reference, the common diacritics are:

1. oxia:  [SIZE=4]**&#940;**[/SIZE]
2. baria: [SIZE=4]**&#8048;**[/SIZE]
3. perspomene: [SIZE=4]**&#8118;**[/SIZE]
4. psili: [SIZE=4]**&#7936;**[/SIZE]
5. daseia: [SIZE=4]**&#7937;**[/SIZE]
6. upogegramene: [SIZE=4]**&#8115;**[/SIZE]

and combinations of these. 

Only the first example above concerns us and only in a specific case.  Everything seems fine at a first glance. But compare 1. (oxia) "**/**" against 2. "**\**"  (baria); obviously #2. is correct, and #1 should be just as slanted as  #2 and in the opposite direction, to the right. Instead, my system picks  up the input from a Greek Polytonic layout and outputs a Tonos "**|**" (straight down) in place of an Oxia "**/**". Even the letter Alpha is different!!! 

Now here's the catch: when I type a combination of a diacritic that  contains the Oxia, my system outputs the Oxia correctly, and does not  give me a Tonos over the vowel!

[SIZE=4]**&#7940;** [SIZE=1](alpha with psili and oxia) [/SIZE][/SIZE]**U+1FFD GREEK OXIA (plus psili plus alpha)** (combination of psili & oxia)
[SIZE=4][SIZE=1]
[SIZE=4]**&#940;**[/SIZE] (alpha with just oxia)[/SIZE][/SIZE]  **U+0301 COMBINING ACUTE ACCENT** or **U+00B4 ACUTE ACCENT** **(plus alpha)** (no combination of diacritics)

(THE UNICODE NUMBERS ABOVE REFER TO THE ACCENT/OXIA _NOT_ THE WHOLE CHARACTER (ACCENT/OXIA AND CHARACTER), BECAUSE THE ACCENTS/OXIA THEMSELVES ARE MODIFIERS, SINCE THEY ARE DEAD KEYS)

There is obviously a problem with the keyboard bindings! The mapping is correct. BUT It should call **U+1FFD GREEK OXIA **instead o f**U+0301 COMBINING ACUTE ACCENT** or **U+00B4 ACUTE ACCENT** when I press the corresponding key.
 ------------------------------------------------------------------------------------------------

After some digging around, I managed to get as far as here, but I'm stuck. Any help would be appreciated.

I want to change the kecode keymap for the   specific key that calls the unicode TONOS/Acute_Accent so that it calls   the unicode Oxeia, BUT **NOT** AFFECT THE USA KEYBOARD LAYOUT. Can I just change the keymap  settings one by one or we  could replace certain things inside **keysymdef.h**.?

The character that the Greek Polytonic Keyboard Layout has assigned for the output of the Oxia is the key  [SIZE=4]**: ;**[/SIZE]  to the left of the Enter key.
It produces** U+0301 COMBINING ACUTE ACCENT** or **U+00B4 ACUTE ACCENT** instead of only just **U+1FFD GREEK OXIA**  using the Greek Polytonic Keyboard layout,  so after a vowel is keyed in, it leads the computer to make use of the  unicode bindings associated only with the Tonos, not the Oxia,  unfortunately. LIke I said, if another diacritic is typed in over the  vowel together with the Tonos or the Oxia, (such as a (Psili, like an  apostrophe), or a daseia (an apostrophe in the oposite direction) or  whatever), the correct unicode block is evoked, and the Tonos is appears  correctly as an Oxia. For reference, I have found that the Tonos is in  the first Unicode Block, while the Oxia is tin the second Unicode block.

--------------------------------------------------------------------------------------------

In my case, the key whose bindings I want to change, is the key that has the   following two symbols on it, (if you use a USA keyboard layout):   [SIZE=6]**: ;**[/SIZE] to the left of the Enter key, like I mentioned earlier.
So, here it goes:
1.  I HAVE IDENTIFIED THE KEYMAP CODE FOR my [SIZE=6]: ;[/SIZE]  KEY. Mine happens to be the number **47**, (after using **xev** in a terminal).

 [B]Keyrelease Event, Serial 36, synthetic NO, window, 0x50000001,
root 0x108, subw 0x0, time 6205231, (65, 109), root: (1102,635),
state 0x0, [COLOR=#ff0000]keycode 47 (keysym 0x3b, semicolon)[/COLOR], same_screen YES,
XLookupString gives 1 bytes: (3b)  "[COLOR=#ff0000];[/COLOR]"
XFilterEvent returns: False[/B]

then I typed in the terminal:
xmodmap -pke | grep 47

and my terminal returns:

[COLOR=#3333ff]keycode  [COLOR=#ff0000]47[/COLOR] = semicolon colon dead_acute dead_abovecomma leftsinglequotemark minutes leftsinglequotemark[/COLOR]
 [COLOR=#3333ff]keycode 1[COLOR=#ff0000]47[/COLOR] = XF86MenuKB NoSymbol XF86MenuKB[/COLOR]
[COLOR=#3333ff]keycode 2[COLOR=#ff0000]47[/COLOR] =[/COLOR]
 
Basically, after reading around I found out that the list that I see  tells me that for Key 47 the following bindings are present, in sequence  of level/modifier:[COLOR=#3333ff]

semicolon [COLOR=#000000](regular keystroke)[/COLOR]
 colon [/COLOR][COLOR=#3333ff][COLOR=#000000](Shift+ keystroke)[/COLOR][/COLOR]
[COLOR=#3333ff] dead_acute [/COLOR][COLOR=#3333ff][COLOR=#000000](AltGr+ keystroke)[/COLOR][/COLOR]
[COLOR=#3333ff] dead_abovecomma [/COLOR][COLOR=#3333ff][COLOR=#000000](AltGr+Shift+ keystroke)[/COLOR][/COLOR]
[COLOR=#3333ff] leftsinglequotemark
 minutes
 leftsinglequotemark[/COLOR]

Fifth, sixth and seventh level I do not know... I thought  keyboards had four  levels of modifiers (Typewriters had only two  (regular and Shift)...so  we are still learning.. .I wonder how those  extra three levels are  accessed... anyway...). 

I assume that the Greek Polytonic basically  accesses the dead_acute and the dead_abovecomma for that particular key  as though they were its first and second level (because when i have  switched to the Greek Polytonic keyboard layout, if i press the key I do  not get a semicolon, but it acts like a dead key, and If I press Shift  and the key I get dead-above comma.... I wonder how the keyboard layout  change basically goes two levels up. Anyway. I Fiddled around trying to  change this list so it would output the Oxia. After much reading around  the internet, I found out I can give it a direct Unicode number instead  of a "mnemonic" name. The changes appear to be  immediate. 
 
 
Then, after I figure all this out,  am I supposed to be able to put my  Oxeia in the third level of symbols to replace the dead_acute so first will  be semicolon, then  colon, then Oxeia, then dead_above comma. 
(OR AM I SUPPOSED TO GO  INTO SOME SECRET HIDDEN FILE SOMEWHERE AND TELL xmodmap THAT WHEN  IT  THINKS IT IS CALLING THE dead_acute, IT SHOULD CALL THE Oxia  INSTEAD???), in any case, 
 I Opened a terminal and I typed: 

[B]xmodmap -e 'keycode 47 = semicolon, colon, U1FFD [COLOR=Black]dead_abovecomma'


[/COLOR][/B][COLOR=Black]But it does not work!!! Now whenever I press the key it is not a dead key!!!! it just displays an Oxia Immediately!!! Obviously it did change t he dead_acute to an Oxia, but how can I make the Oxia a dead_acute too or just dead???!
How can I make it see U1FFD as a dead key? [/COLOR]**[COLOR=Black]In the character map [/COLOR]**[COLOR=Black]it says that the Oxia U1FFD is a dead key/modifier. So what is going on?? [/COLOR][B][COLOR=Black]
[/COLOR][/B] 

I only want to change the output for the Greek Polytonic Keyboard layout!!! or perhaps I WANT TO CHANGE THE BINDING FOR ONE KEY ON THE GREEK POLYTONIC KEYBOARD LAYOUT 

    (WHERE IS THE FILE FOR THIS KEYOBOARD LAYOUT SAVED IN UBUNTU? AND HOW  DOES IT ACCESS keysymdef.h OR DOES IT? And how to I change it??

 [SIZE=3]Is there a way to just do this, but so that it affects  only the Greek Polytonic keyboard layout and not my USA keyboard layout,  and so that "**xxxxx_xxxx**" [/SIZE](see below)[SIZE=3] calls the Polytonic Unicode character called Oxia, found in the second unicode block, known as [/SIZE][SIZE=3][COLOR=#3333ff]U+1FFD GREEK OXIA[/COLOR][/SIZE][SIZE=3] :[/SIZE]
 

**xmodmap -e 'keycode 47 = semicolon, colon, xxxxx_xxxx [COLOR=Black]dead_abovecomma leftsinglequotemark '[/COLOR]**

I don't know what the hell to type there, obviously the **dead_acute** didn't work, because it evokes a tonos!!! I need to tell it that whe I type dead_acute, it calls U1FFD (the oxia). I tried typing **oxia**,  and random jarble, but it returns an error (How do i know what Oxia is  called -- what's the mnemonic name/code for it other than the unicode number  U1FFD? It is not anywhere to be found in the keysymdef.h file  can i create it? How?). I think what needs to be done is tell it to call **[SIZE=1][COLOR=Black]U+1FFD GREEK OXIA[/COLOR][/SIZE]** even though it thinks it is calling **dead_acute, **because right now the **dead_acute **is actually calling a Tonos, possibly [COLOR=#3333ff][SIZE=1][COLOR=DimGray]U+00B4 ACUTE ACCENT,[/COLOR][/SIZE][SIZE=2][COLOR=Black]which I don't want!!![/COLOR][/SIZE][/COLOR]
 

[SIZE=4]Thank you for even taking the time to read through this.

Any help you can provide me with would be greatly appreciated!!!

Dimitris.[/SIZE]



P.S.1
[COLOR=#3333ff]I installed [/COLOR]**x11proto-core-dev, **[COLOR=#3333ff]("[/COLOR]**sudo apt-get install x11proto-core-dev**[COLOR=#3333ff]")  without the quotes. Then after some digging around, I finally found the [/COLOR]** Keysym**[COLOR=#3333ff]  lists that we need in order to assign the correct name, I mean, I  call  it Oxeia, you call it Oxia, and the Kesyms list may have it as   OXEIA_Greek_Unicode, or called it Funny_Looking_FrontSlash, I don't  know, we are looking for the mnemonic name  or the number that  corresponds to the Oxeia. So anyway, this list should is in the file: "[/COLOR]**/usr/include/X11/keysymdef.h**[COLOR=#3333ff]" without the quotes. There I read:[/COLOR]
   
 [COLOR=#3333ff] Can somebody tell me please [/COLOR](the following instructions were in the keysymdef.h file)
  [COLOR=Black][COLOR=#3333ff]1. How do I add [/COLOR][/COLOR][COLOR=Black][COLOR=#3333ff]0x01000000 to[SIZE=1][SIZE=2]U+1FFD ?[/SIZE][/SIZE][/COLOR][/COLOR][COLOR=#3333ff]  (Are these Hexadecimal values?) and how do I type this value instead of  a name (such as dead_accent) or whatever into xmodmasp for a key  corresponding to the Oxia and not the Tonos???[/COLOR]
 [COLOR=#3333ff] 2. How do I update [/COLOR][COLOR=Black][COLOR=#3333ff]the mappings in src/KeyBind.c in the repo[/COLOR][/COLOR][COLOR=#3333ff]? [/COLOR][COLOR=Black][COLOR=#3333ff](what is Repo? does it mean repository?) and the protocol specification in specs/XProtocol/X11.keysyms[/COLOR][/COLOR][COLOR=#3333ff] that it mentions in that file??? and Why?[/COLOR]
  [COLOR=#3333ff] 3. What are [/COLOR][COLOR=#000066][COLOR=#3333ff]XStringToKeysym() and XKeysymToString().[/COLOR][/COLOR][COLOR=#3333ff] and how do I use them?[/COLOR]
  [COLOR=#3333ff] 4. How do I change things in this file keysymdef.h directly? I also read  somewhere that someone can change the keyboard layout file as well. I  found it in[/COLOR]
  
 [COLOR=#3333ff] In any case...[/COLOR]
  geeez, sometimes i hate Linux...





P.S.2
Below I have pasted the information that you may need in order to be able to help me out.
----------------------------------
THE CHARACTERS IN  QUESTION FROM THE CHARACTER MAP REVEALS  THE PROBLEM: UNICODE  CONSIDERS THE OXEIA AND THE TONOS  INTERCHANGEABLE/EQUIVALENT.
----------------------------------
[HTML]&#943;

U+03AF GREEK SMALL LETTER IOTA WITH TONOS
 
General Character Properties
In Unicode since: 1.1
 Unicode category: Letter, Lowercase
Canonical decomposition: U+03B9 GREEK SMALL LETTER IOTA + U+0301 COMBINING ACUTE ACCENT
 
Various Useful Representations
UTF-8: 0xCE 0xAF
 UTF-16: 0x03AF
C octal escaped UTF-8: \316\257
XML decimal entity: &#943;
 
Annotations and Cross References
Equivalents:
  • U+03B9 GREEK SMALL LETTER IOTA U+0301 COMBINING ACUTE ACCENT

----------------------------------

&#8055;
 
U+1F77 GREEK SMALL LETTER IOTA WITH OXIA

General Character Properties
 In Unicode since: 1.1
Unicode category: Letter, Lowercase
 Canonical decomposition: U+03B9 GREEK SMALL LETTER IOTA + U+0301 COMBINING ACUTE ACCENT

 Various Useful Representations
UTF-8: 0xE1 0xBD 0xB7
UTF-16: 0x1F77
 C octal escaped UTF-8: \341\275\267
XML decimal entity: &#8055;
 
Annotations and Cross References
Equivalents:
  • U+03AF GREEK SMALL LETTER IOTA WITH TONOS greek small letter iota with tonos

----------------------------------


´
 U+00B4 ACUTE ACCENT (WE DON'T WANT THIS ONE, THIS ONE CAUSES THE PROBLEM, found in keysymdef.h)

General Character Properties
 In Unicode since: 1.1
Unicode category: Symbol, Modifier
 
Various Useful Representations
UTF-8: 0xC2 0xB4
 UTF-16: 0x00B4
C octal escaped UTF-8: \302\264
XML decimal entity: ´
 
Annotations and Cross References
Notes:
  • this is a spacing character

See also:
  • U+02B9 MODIFIER LETTER PRIME
 • U+02CA MODIFIER LETTER ACUTE ACCENT
  • U+0301 COMBINING ACUTE ACCENT
 • U+2032 PRIME

 Approximate equivalents:
 • U+0020 SPACE U+0301 COMBINING ACUTE ACCENT

----------------------------------

 *&#769;
U+0301 COMBINING ACUTE ACCENT  (WE DON'T WANT THIS ONE, THIS ONE CAUSES THE PROBLEM, found in  keysymdef.h) (ignore the asterisk, I don't know why it comes up there - I  can't remove it)
 
General Character Properties
In Unicode since: 1.1
 Unicode category: Mark, Non-Spacing

Various Useful Representations
 UTF-8: 0xCC 0x81
UTF-16: 0x0301

 C octal escaped UTF-8: \314\201
XML decimal entity: &#769;
 
Annotations and Cross References
Alias names:
  • stress mark
 • Greek oxia, tonos

 See also:
 • U+0027 APOSTROPHE
 • U+00B4 ACUTE ACCENT
  • U+02B9 MODIFIER LETTER PRIME
 • U+02CA MODIFIER LETTER ACUTE ACCENT
  • U+0384 GREEK TONOS
----------------------------------

&#8189;
 U+1FFD GREEK OXIA (WE WANT THIS ONE, THE ONE THE SPELLCHECKER RECOGNIZES, not found in keysymdef.h)

General Character Properties
 In Unicode since: 1.1
Unicode category: Symbol, Modifier
 
Various Useful Representations
UTF-8: 0xE1 0xBF 0xBD
 UTF-16: 0x1FFD

C octal escaped UTF-8: \341\277\275
 XML decimal entity: &#8189;
Annotations and Cross References
 
Equivalents:
 • U+00B4 ACUTE ACCENT acute accent (obviously NOT an equivalent!!! duh, way to go unicode people...)

(WE WANT THE ONE ABOVE. A SIMPLE TEST PROVES THIS (I opened  OpenOffice and typed the  word &#8017;&#947;&#949;&#943;&#945; using the extended Greek special  characters from the Insert  character menu (not my keyboard) and the  spellchecker found it to be  correct).
----------------------------------

&#714;
U+02CA MODIFIER LETTER ACUTE ACCENT (MIGHT WORK, NOT SURE, DEPENDS)
 
General Character Properties
In Unicode since: 1.1
 Unicode category: Letter, Modifier

Various Useful Representations
 UTF-8: 0xCB 0x8A
UTF-16: 0x02CA
C octal escaped UTF-8: \313\212
 XML decimal entity: &#714;

Annotations and Cross References
 Notes:
 • high-rising tone (IPA), high tone, primary stress
  • Mandarin Chinese second tone[/HTML]

---

### Post by ellaivarios on 2011-06-29
Ok, I tried 

[HTML]xmodmap -e 'keycode 47 = semicolon, colon, U1FFD dead_abovecomma leftsinglequotemark '[/HTML]

it seems to be what I have to do, and it sure does output an Oxia when I use the Polytonic Greek Keyboard BUT

IT IS NOT A DEAD KEY ANyMORE!!!! For the love of god. It just outputs an Oxia as soon as I type the key. How can I make it a dead key???

Guys Please, any ideas??? Anyone?? Please!!!

---

### Post by ellaivarios on 2011-07-01
I found the compose file in /usr/share/X11/locale/iso8859-15/Compose
which appears to be the Greek (Polytonic?) keyboard layout Locale. So how do I change it from calling th TONOS to calling the OXIA by making it call Unicode U1FFD whenever I press the key that is assigned to call the dead_acute, but still treat it as a DEAD key??

What do I need to change in this file?? any ideas??

[HTML]# $TOG: iso8859-7 /main/7 1998/05/20 15:33:23 kaleb $
#
# ISO 8859-7 (Greek) Compose Sequence
#
#
# $XFree86: xc/nls/Compose/iso8859-7,v 1.4 2001/04/26 21:09:40 dawes Exp $
#
# Sequence Definition
#
# <Multi_key> Means <Compose>
# Special Character
<Multi_key> <plus> <plus>        : "#"    numbersign
<Multi_key> <apostrophe> <space>    : "'"    apostrophe
<Multi_key> <space> <apostrophe>    : "'"    apostrophe
<Multi_key> <A> <T>            : "@"    at
<Multi_key> <parenleft> <parenleft>    : "["    bracketleft
<Multi_key> <slash> <slash>        : "\\"    backslash
<Multi_key> <slash> <less>        : "\\"    backslash
<Multi_key> <less> <slash>        : "\\"    backslash
<Multi_key> <parenright> <parenright>    : "]"    bracketright
<Multi_key> <asciicircum> <space>    : "^"    asciicircum
<Multi_key> <space> <asciicircum>    : "^"    asciicircum
<Multi_key> <greater> <space>        : "^"    asciicircum
<Multi_key> <space> <greater>        : "^"    asciicircum
<Multi_key> <grave> <space>        : "`"    grave
<Multi_key> <space> <grave>        : "`"    grave
<Multi_key> <parenleft> <minus>        : "{"    braceleft
<Multi_key> <minus> <parenleft>        : "{"    braceleft
<Multi_key> <slash> <asciicircum>    : "|"    bar
<Multi_key> <asciicircum> <slash>    : "|"    bar
<Multi_key> <V> <L>            : "|"    bar
<Multi_key> <L> <V>            : "|"    bar
<Multi_key> <v> <l>            : "|"    bar
<Multi_key> <l> <v>            : "|"    bar
<Multi_key> <parenright> <minus>    : "}"    braceright
<Multi_key> <minus> <parenright>    : "}"    braceright
<Multi_key> <asciitilde> <space>    : "~"    asciitilde
<Multi_key> <space> <asciitilde>    : "~"    asciitilde
<Multi_key> <minus> <space>        : "~"    asciitilde
<Multi_key> <space> <minus>        : "~"    asciitilde

<Multi_key> <l> <minus>            : "\243"    sterling
<Multi_key> <minus> <l>            : "\243"    sterling
<Multi_key> <L> <minus>            : "\243"    sterling
<Multi_key> <minus> <L>            : "\243"    sterling
<Multi_key> <l> <equal>            : "\243"    sterling
<Multi_key> <equal> <l>            : "\243"    sterling
<Multi_key> <L> <equal>            : "\243"    sterling
<Multi_key> <equal> <L>            : "\243"    sterling
<Multi_key> <s> <o>            : "\247"    section
<Multi_key> <o> <s>            : "\247"    section
<Multi_key> <S> <O>            : "\247"    section
<Multi_key> <O> <S>            : "\247"    section
<Multi_key> <S> <exclam>        : "\247"    section
<Multi_key> <exclam> <S>        : "\247"    section
<Multi_key> <s> <exclam>        : "\247"    section
<Multi_key> <exclam> <s>        : "\247"    section
<Multi_key> <S> <0>            : "\247"    section
<Multi_key> <0> <S>            : "\247"    section
<Multi_key> <s> <0>            : "\247"    section
<Multi_key> <0> <s>            : "\247"    section
<Multi_key> <c> <o>            : "\251"    copyright
<Multi_key> <o> <c>            : "\251"    copyright
<Multi_key> <C> <O>            : "\251"    copyright
<Multi_key> <O> <C>            : "\251"    copyright
<Multi_key> <c> <O>            : "\251"    copyright
<Multi_key> <O> <c>            : "\251"    copyright
<Multi_key> <C> <o>            : "\251"    copyright
<Multi_key> <o> <C>            : "\251"    copyright
<Multi_key> <c> <0>            : "\251"    copyright
<Multi_key> <0> <c>            : "\251"    copyright
<Multi_key> <C> <0>            : "\251"    copyright
<Multi_key> <0> <C>            : "\251"    copyright
<Multi_key> <parenleft> <c>        : "\251"    copyright
<Multi_key> <less> <less>        : "\253"    guillemotleft
<Multi_key> <greater> <greater>        : "\273"    guillemotright
<Multi_key> <0> <asciicircum>        : "\260"    degree
<Multi_key> <asciicircum> <0>        : "\260"    degree
<Multi_key> <0> <asterisk>        : "\260"    degree
<Multi_key> <asterisk> <0>        : "\260"    degree
<Multi_key> <plus> <minus>        : "\261"    plusminus
<Multi_key> <minus> <plus>        : "\261"    plusminus
<Multi_key> <2> <asciicircum>        : "\262"    twosuperior
<Multi_key> <asciicircum> <2>        : "\262"    twosuperior
<Multi_key> <S> <2>            : "\262"    twosuperior
<Multi_key> <2> <S>            : "\262"    twosuperior
<Multi_key> <s> <2>            : "\262"    twosuperior
<Multi_key> <2> <s>            : "\262"    twosuperior
<Multi_key> <3> <asciicircum>        : "\263"    threesuperior
<Multi_key> <asciicircum> <3>        : "\263"    threesuperior
<Multi_key> <S> <3>            : "\263"    threesuperior
<Multi_key> <3> <S>            : "\263"    threesuperior
<Multi_key> <s> <3>            : "\263"    threesuperior
<Multi_key> <3> <s>            : "\263"    threesuperior
<Multi_key> <period> <asciicircum>    : "\267"    periodcentered
<Multi_key> <asciicircum> <period>    : "\267"    periodcentered
<Multi_key> <period> <period>        : "\267"    periodcentered
<Multi_key> <1> <2>            : "\275"    onehalf
<Multi_key> <space> <space>        : "\240"    nobreakspace
<Multi_key> <bar> <bar>            : "\246"    brokenbar
<Multi_key> <exclam> <asciicircum>    : "\246"    brokenbar
<Multi_key> <asciicircum> <exclam>    : "\246"    brokenbar
<Multi_key> <V> <B>            : "\246"    brokenbar
<Multi_key> <B> <V>            : "\246"    brokenbar
<Multi_key> <v> <b>            : "\246"    brokenbar
<Multi_key> <b> <v>            : "\246"    brokenbar
<Multi_key> <minus> <comma>        : "\254"    notsign
<Multi_key> <comma> <minus>        : "\254"    notsign
<Multi_key> <minus> <minus>        : "\255"    hyphen
# should be Greek tonos but not defined in X11
<Multi_key> <apostrophe> <apostrophe>    : "\264"    acute
# should be Greek dialytika but not defined in X11
<Multi_key> <quotedbl> <quotedbl>    : "\250"    diaeresis
# special characters that don't exist in Latin-1
<Multi_key> <less> <apostrophe>        : "\241"    leftsinglequotemark
<Multi_key> <apostrophe> <less>        : "\241"    leftsinglequotemark
<Multi_key> <greater> <apostrophe>    : "\242"    rightsinglequotemark
<Multi_key> <apostrophe> <greater>    : "\242"    rightsinglequotemark
<Multi_key> <asciitilde> <asciitilde>    : "\257"    Greek_horizbar

# Accented Alphabet
<Multi_key> <Greek_ALPHA> <apostrophe>    : "\266" Greek_ALPHAaccent
<Multi_key> <apostrophe> <Greek_ALPHA>    : "\266" Greek_ALPHAaccent
<Multi_key> <Greek_EPSILON> <apostrophe>: "\270" Greek_EPSILONaccent
<Multi_key> <apostrophe> <Greek_EPSILON>: "\270" Greek_EPSILONaccent
<Multi_key> <Greek_ETA> <apostrophe>    : "\271" Greek_ETAaccent
<Multi_key> <apostrophe> <Greek_ETA>    : "\271" Greek_ETAaccent
<Multi_key> <Greek_IOTA> <apostrophe>    : "\272" Greek_IOTAaccent
<Multi_key> <apostrophe> <Greek_IOTA>    : "\272" Greek_IOTAaccent
<Multi_key> <Greek_OMICRON> <apostrophe>: "\274" Greek_OMICRONaccent
<Multi_key> <apostrophe> <Greek_OMICRON>: "\274" Greek_OMICRONaccent
<Multi_key> <Greek_UPSILON> <apostrophe>: "\276" Greek_UPSILONaccent
<Multi_key> <apostrophe> <Greek_UPSILON>: "\276" Greek_UPSILONaccent
<Multi_key> <Greek_OMEGA> <apostrophe>    : "\277" Greek_OMEGAaccent
<Multi_key> <apostrophe> <Greek_OMEGA>    : "\277" Greek_OMEGAaccent
<Multi_key> <Greek_IOTA> <quotedbl>    : "\332" Greek_IOTAdieresis
<Multi_key> <quotedbl> <Greek_IOTA>    : "\332" Greek_IOTAdieresis
<Multi_key> <Greek_UPSILON> <quotedbl>    : "\333" Greek_UPSILONdieresis
<Multi_key> <quotedbl> <Greek_UPSILON>    : "\333" Greek_UPSILONdieresis

<Multi_key> <Greek_alpha> <apostrophe>    : "\334" Greek_alphaaccent
<Multi_key> <apostrophe> <Greek_alpha>    : "\334" Greek_alphaaccent
<Multi_key> <Greek_epsilon> <apostrophe>: "\335" Greek_epsilonaccent
<Multi_key> <apostrophe> <Greek_epsilon>: "\335" Greek_epsilonaccent
<Multi_key> <Greek_eta> <apostrophe>    : "\336" Greek_etaaccent
<Multi_key> <apostrophe> <Greek_eta>    : "\336" Greek_etaaccent
<Multi_key> <Greek_iota> <apostrophe>    : "\337" Greek_iotaaccent
<Multi_key> <apostrophe> <Greek_iota>    : "\337" Greek_iotaaccent
<Multi_key> <Greek_omicron> <apostrophe>: "\374" Greek_omicronaccent
<Multi_key> <apostrophe> <Greek_omicron>: "\374" Greek_omicronaccent
<Multi_key> <Greek_upsilon> <apostrophe>: "\375" Greek_upsilonaccent
<Multi_key> <apostrophe> <Greek_upsilon>: "\375" Greek_upsilonaccent
<Multi_key> <Greek_omega> <apostrophe>    : "\376" Greek_omegaaccent
<Multi_key> <apostrophe> <Greek_omega>    : "\376" Greek_omegaaccent
<Multi_key> <Greek_iota> <quotedbl>    : "\372" Greek_iotadieresis
<Multi_key> <quotedbl> <Greek_iota>    : "\372" Greek_iotadieresis
<Multi_key> <Greek_upsilon> <quotedbl>    : "\373" Greek_upsilondieresis
<Multi_key> <quotedbl> <Greek_upsilon>    : "\373" Greek_upsilondieresis

<Multi_key> <apostrophe> <quotedbl> <Greek_iota>    : "\300" Greek_iotaaccentdieresis
<Multi_key> <quotedbl> <apostrophe> <Greek_iota>    : "\300" Greek_iotaaccentdieresis
<Multi_key> <apostrophe> <quotedbl> <Greek_upsilon>    : "\340" Greek_upsilonaccentdieresis
<Multi_key> <quotedbl> <apostrophe> <Greek_upsilon>    : "\340" Greek_upsilonaccentdieresis
<Multi_key> <apostrophe> <quotedbl> <space>        : "\265" Greek_accentdieresis
<Multi_key> <quotedbl> <apostrophe> <space>        : "\265" Greek_accentdieresis

#
#
# dead key accent keysyms
# Special Character
<dead_circumflex> <slash>        : "|"    bar
<dead_grave> <space>            : "`"    grave
<dead_diaeresis> <space>        : "\250"    diaeresis
<dead_circumflex> <space>        : "^"    asciicircum
<dead_tilde> <space>            : "~"    asciitilde
<dead_doubleacute> <space>        : "\""    quotedbl
<dead_abovering> <space>        : "\260"    degree
<dead_abovering> <dead_abovering>    : "\260"    degree
<dead_circumflex> <0>            : "\260"    degree
<dead_circumflex> <2>            : "\262"    twosuperior
<dead_circumflex> <3>            : "\263"    threesuperior
<dead_circumflex> <period>        : "\267"    periodcentered
<dead_circumflex> <exclam>        : "\246"    brokenbar
<dead_cedilla> <minus>            : "\254"    notsign
<dead_acute> <apostrophe>        : "\264"    acute
<dead_diaeresis> <quotedbl>        : "\250"    diaeresis

# Accented Alphabet (plus some more symbols)
<dead_acute> <Greek_alpha>        : "\334"    Greek_alphaaccent
<dead_acute> <Greek_epsilon>        : "\335"    Greek_epsilonaccent
<dead_acute> <Greek_eta>        : "\336"    Greek_etaaccent
<dead_acute> <Greek_iota>        : "\337"    Greek_iotaaccent
<dead_acute> <Greek_omicron>        : "\374"    Greek_omicronaccent
<dead_acute> <Greek_upsilon>        : "\375"    Greek_upsilonaccent
<dead_acute> <Greek_omega>        : "\376"    Greek_omegaaccent
<dead_acute> <Greek_ALPHA>        : "\266"    Greek_ALPHAaccent
<dead_acute> <Greek_EPSILON>        : "\270"    Greek_EPSILONaccent
<dead_acute> <Greek_ETA>        : "\271"    Greek_ETAaccent
<dead_acute> <Greek_IOTA>        : "\272"    Greek_IOTAaccent
<dead_acute> <Greek_OMICRON>        : "\274"    Greek_OMICRONaccent
<dead_acute> <Greek_UPSILON>        : "\276"    Greek_UPSILONaccent
<dead_acute> <Greek_OMEGA>        : "\277"    Greek_OMEGAaccent
<dead_acute> <space>            : "\264"    acute
<dead_acute> <dead_acute>        : "\264"    acute
<dead_acute> <period>            : "\267"    periodcentered
<dead_acute> <less>            : "\253"    guillemotleft
<dead_acute> <greater>            : "\273"    guillemotright

<dead_diaeresis> <Greek_iota>        : "\372"    Greek_iotadieresis
<dead_diaeresis> <Greek_upsilon>    : "\373"    Greek_upsilondieresis
<dead_diaeresis> <Greek_IOTA>        : "\332"    Greek_IOTAdieresis
<dead_diaeresis> <Greek_UPSILON>    : "\333"    Greek_UPSILONdieresis
<dead_diaeresis> <dead_diaeresis>    : "\250"    diaeresis
<dead_diaeresis> <period>        : "\267"    periodcentered
<dead_diaeresis> <less>            : "\253"    guillemotleft
<dead_diaeresis> <greater>        : "\273"    guillemotright

<dead_acute> <dead_diaeresis> <Greek_iota>    : "\300"    Greek_iotaaccentdieresis
<dead_acute> <dead_diaeresis> <Greek_upsilon>    : "\340"    Greek_upsilonaccentdieresis
<dead_acute> <dead_diaeresis> <space>        : "\265"    Greek_accentdieresis

<dead_diaeresis> <dead_acute> <Greek_iota>    : "\300"    Greek_iotaaccentdieresis
<dead_diaeresis> <dead_acute> <Greek_upsilon>    : "\340"    Greek_upsilonaccentdieresis
<dead_diaeresis> <dead_acute> <space>        : "\265"    Greek_accentdieresis
[/HTML]

---

