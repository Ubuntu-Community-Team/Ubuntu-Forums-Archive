---
title: "gettext not working?"
date: 2010-07-28
forum: General Help
---

### Post by worksofcraft on 2010-07-28
I'm trying to learn about internationalization for software I hope  to develop.

Thus I follow tutorial [http://oriya.sarovar.org/docs/gettext_single.html](http://oriya.sarovar.org/docs/gettext_single.html) about using GNU gettext.

I make the traditional "hello world" program as per instructions, but when I get to the bit where it says " ./hello should now give you output in Oriya"... well mine still just says "Hello, world!" instead of "&#2856;&#2862;&#2872;&#2893;&#2837;&#2878;&#2864;\n"

anyone have any ideas where I'm going wrong?

---

### Post by worksofcraft on 2010-07-28
I seem to have solved that, by running:

sudo locale-gen or_IN
export LANG=or_IN

... and then my 'hello world' program is speaking Oriya :)

However I suspect I'll find a few more issues before I fully understand it. I'll keep this thread open for others who are starting to explore i18n and l10n on Ubuntu :)

---

### Post by worksofcraft on 2010-07-28
That's all well and good for the trivial case of
[I]
	printf( gettext( "Hello, world!\n" ) );
[/I]

however progressing with slightly more versatile code structures such as:[I]

static const char msg[] = "Hello, world!\n";
...
	printf( gettext(msg) );
[/I]

I discover that this string no longer is included for translation :shock:

Perhaps jumping the gun a bit here, but I would like to hear how others experience programming with internationalization in mind?

---

### Post by worksofcraft on 2010-07-29
besides identifying language, 'locale' identify things like currency symbols and numeric formats. This information we can get with function localeconv() in C and similar languages and so I created a little program called a.out to test it:

$> export LANG=en_GB
$> ./a.out
Local Currency Symbol: &#65533;
International Currency Symbol: GBP

$> export LANG=fr_FR
$> ./a.out
Local Currency Symbol: EUR
International Currency Symbol: EUR 

 :-\" but what about £ and € symbols I wondered?

 Just in case anyone else struggles with this: The answer is to specify UTF-8 encoding (hopefully that becomes the default one day):

$> export LANG=en_GB.UTF-8
$> ./a.out
Local Currency Symbol: £
International Currency Symbol: GBP 
$> export LANG=fr_FR.UTF-8
$> ./a.out
Local Currency Symbol: €
International Currency Symbol: EUR

If you just get blanks you must create support for the locale on your computer first, e.g. Welsh locale:

$> export LANG=cy_GB.UTF-8
$> ./a.out
Local Currency Symbol: 
International Currency Symbol: 
$> sudo locale-gen cy_GB.UTF-8
Generating locales...
  cy_GB.UTF-8... done
Generation complete.
$> ./a.out
Local Currency Symbol: £
International Currency Symbol: GBP

---

### Post by worksofcraft on 2010-07-29
BTW just in case you wonder why the language didn't change in my a.out... well I did consider doing the whole "gettext" as an exercise but my  French is very rusty and my Welsh non-existent, so I tried a free online translator:

"Local Currency Symbol"
in French became
"Symbole de Devise locale"
and in Welsh
"n lleol Arian Breiniol Arwyddlun"
but translating it back to English and I get
"Symbol of local Motto"
and
"heartburn local Currency Emblem"

lol... I think the French and the Welsh might appreciate my attempt, but I also think they are probably quite pleased I decided not to :D

---

### Post by worksofcraft on 2010-08-03
for the sake of completeness this solution to afore mentioned problem  with static tables of strings:

Evidently if you wrote:
static const char msg[] = gettext("Hello, world!\n");
Then the string IS included for translation, but gcc compiler objects with - hello.c:7: error: invalid initializer

so what you do is:

// table of static strings where dummy gettext() serves only
// to identify translatable strings to the gettext tools.
#define gettext(s) s
static const char msg[] = gettext("Hello, world!\n");
#undef gettext

elsewhere in your program at run time the actual translation takes place where you call the real gettext()
	printf( gettext(msg) );

I was thinking of writing some kind of summary/totarial but IDK where to put it as it's not really specific interest to Ubuntu community.

So just one word of caution: msginit prompts to include your e-mail address into portable object files, but beware of placing these on the web as you may then be targeted for spam by e-mail harvesting bots :-$

---

### Post by worksofcraft on 2010-08-04
Moving on from straight C to combine Python with a Glade GUI, don't forget to also bind text domain for glade module or the GUI won't use your translated strings!
```

		for module in (gettext, gtk.glade):	
			module.bindtextdomain('pyHello', '/usr/share/locale')
			module.textdomain('pyHello')

```

p.s. ok I think I got the hang of gettext now :)
... if you need help with iternationalization you can post here

---

### Post by worksofcraft on 2010-08-08
Problems of internationalization are really fascinating.
Like have you ever phones the speaking clock?

"At the 3rd beep, it will be 1 minute past 12"

And a C++ programmer might think he/she is doing a good job coding it:
```

   cout << "At the " << beep << ord[beep % 10] << " beep, it will be " <<
   minute << ((minute!=1)?" minutes":" minute")<<" past " <<
   hour << endl;

```

However the Dutch translation team needs to change it to read:

"Aan de 3de fluittoon zal het 1 minuut voorbij 12 zijn"
so exactly how can they get that final "zijn" in to there and can they fathom translating the 'rd' appended algorithmically to 3rd into 'de'?

Meanwhile next door French translation team is trying to make it say: 
"Au troisième bip, ce sera 12 heures 1"
but they can't work out why it keeps telling them it's 12 minutes past 1 :O

so you see if you do want software you develop to be amenable to localization there are some do's and don'ts to be considered ;)

Can anyone suggest good place to post my tutorial I'm writing?

---

