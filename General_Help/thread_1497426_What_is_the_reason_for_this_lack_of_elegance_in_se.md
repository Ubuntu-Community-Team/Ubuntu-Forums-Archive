---
title: "What is the reason for this lack of elegance in sed?"
date: 2010-05-30
forum: General Help
---

### Post by HotForLinux on 2010-05-30
Is this a bug or just...

```
**$ echo aaaxbbb | sed 's/x/\n/'| sed 's/\n/x/'**
aaa
bbb

```An inverse subtitution should give as a result:
```

aaaxbbb

```don't you think?

---

### Post by ibuclaw on 2010-05-30
sed processes text on a "per line" basis, so you cannot match newlines in sed without appending the next line of input into the pattern space.

```
echo aaaxbbb | sed 's/x/\n/'| sed '**N;**s/\n/x/'
```
Even then, that isn't without it's faults.


Question, Why not use Perl instead? :)

Regards
Iain

---

### Post by HotForLinux on 2010-05-30
> **ibuclaw said:**
> sed processes text on a "per line" basis, so you cannot match newlines in sed without appending the next line of input into the pattern space.

```
echo aaaxbbb | sed 's/x/\n/'| sed '**N;**s/\n/x/'
```Even then, that isn't without it's faults.


Question, Why not use Perl instead? :)

Regards
Iain


Well that's a good reason. But there should be a command or an option thats replaces strings on a "charactrer stream " basis, don't you think?
Yes, maybe I should study again/more perl. It is just that I feel that would be using a cannon to kill flies.

```
$ echo aaaxbbb | sed 's/x/\n\n\n/'| sed 'N;s/\n/x/'
aaax
xbbb

```

---

### Post by ibuclaw on 2010-05-30
> **HotForLinux said:**
> Yes, maybe I should study again/more perl. It is just that I feel that would be using a cannon to kill flies.


Perl is hardly a cannon... Yes it is powerful, but it isn't heavyweight.

[http://blog.ksplice.com/2010/05/top-10-perl-one-liner-tricks/](http://blog.ksplice.com/2010/05/top-10-perl-one-liner-tricks/)

Regards

---

### Post by HotForLinux on 2010-05-30
> **ibuclaw said:**
> Perl is hardly a cannon... Yes it is powerful, but it isn't heavyweight.

[http://blog.ksplice.com/2010/05/top-10-perl-one-liner-tricks/](http://blog.ksplice.com/2010/05/top-10-perl-one-liner-tricks/)

Regards


So we will have:
1. Behaving like sed, 'per line':
```
**$ echo -n "aaaxbbbxxxx"|perl -pe 's/x/\n/g'|[COLOR=Indigo]perl -[/COLOR][COLOR=Indigo]lpe 's/\n/x/g'[/COLOR]**
aaa
bbb



**$**
```But also, processing a stream of chars:
```
**$ echo -n "aaaxbbbxxxx"|perl -pe 's/x/\n/g'|[COLOR=Indigo]perl -pe 's/\n/x/'[/COLOR]**
aaaxbbbxxxx**$**
```
 
Is that what you mean (for example)?
Yes, works fine. 
Thanx!

---

