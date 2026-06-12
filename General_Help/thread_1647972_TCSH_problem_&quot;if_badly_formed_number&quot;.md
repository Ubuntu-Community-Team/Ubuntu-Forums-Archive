---
title: "TCSH problem: &quot;if: badly formed number&quot;"
date: 2010-12-18
forum: General Help
---

### Post by geo132 on 2010-12-18
Hey guys, i'm working on homework about C-Shell, i wrote a script which takes a date and extracts the year. date format can be "dd.mm.yyyy" in this case i print yyyy, or "dd.mm.yy", in this case:
if 0<=yy<15 print 20yy
else if 15<=yy<99 print 19yy
examples:
18.12.10 ---> 2010 
18.12.14 ---> 2014 
18.12.08 ---> 2008 
18.12.2008 ----> 2008 
18.12.17 ----> 1917 
I'm getting a problem when i enter "08" or "09". i get error badly formed number.
I've ran the script on other machines and they work great, but on mine i get the problem.
Any idea how to fix it?
script:
```
#!/bin/tcsh -f
set line = ($<)

set temp = `echo $line | cut -d"." -f3`

if( $temp >= 0 && $temp < 15) then
    echo 20$temp
else 
    if( $temp >= 15 && $temp <= 99) then
    echo 19$temp
    else echo $temp
endif
endif

```Thanks in advance and happy holidays,
Geo

---

### Post by geo132 on 2010-12-20
Sorry for bumping the toipc, but i kind of need help in this matter and i don't see any other place where i can find a solutioin.

---

### Post by x1a4 on 2010-12-20
Hi,

The problem is cut: 
```
set temp = `echo $line | cut **-d"."** -f3`
```
You're checking for "." but have probably used a comma or dash or anything other than a period to separate day/month/year in your input.  If you use a period it should work (at least it does on my end).  You're probably better off using awk instead of cut.  With cut you can only use one delimiter, so unless you want to join multiple cut statements (very dirty) you should use awk.

---

### Post by geo132 on 2010-12-20
Cheers for the answer, though i doubt the problem is with my input. I have tried manually typing it and via file yet the problem exists either way. Could it be a problem with my tcsh? I have tried it on another machine running Ubuntu and it failed as well, yet if i run it on a machine running linux (server we need to perform our tests on) it works correctly. I guess that limits the problem a bit more..

---

### Post by x1a4 on 2010-12-20
Interesting problem.  You should compare tcsh versions and configuration on your test box and the others to see what's different.  You code is good (see attached screenshot), so you may be right and it is something with tcsh itself.  

Below is my tcsh (v6.14.00 from Hardy repos) configuration for comparison. 

```

# ~/.tcshrc.set

## TCSH CONFIG 

# set prompt      = '[%{[01;32m%}'${USER}'%{[01;31m%}:%{[01;36m%}tcsh%{[00m%}]%{[01;34m%}%c02/%{[01;32m%}%%%{[00m%} '
set prompt      = '[%{[01;36m%}tcsh%{[00m%}]%{[01;34m%}%c02/%{[01;32m%}%%%{[00m%} '
set prompt2     = '%R%{[01;33m%}>%{[00m%} '
set prompt3     = '%{[01;35m%}CORRECT>%{[01;37m%}%R%{[01;35m%}(ynea)%{[01;33m%}?%{[00m%} '
set rprompt     = '%{[01;35m%}<%m:%s:%ms'
set promptchars = '$%#'
set history     =  50
set savehist    = (50 merge)
set histfile    = ${HOME}/.tcsh_histfile
set histdup     =  erase
set savedirs    =  5
set dirsfile    = ${HOME}/.tcsh_dirsfile
set matchbeep   =  nomatch
set inputmode   =  insert
set complete    =  enhance
                 # all complete cmd
set correct     =  complete
set symlinks    =  chase
set listjobs    =  long
set fignore     = (.o \~ CVS RCS)
set echo_style  =  both
set killring    =  25
set listmax     =  25
set listmaxrows =  25
set sched       = '%h\t%T\t%R\n'
set wordchars   = '~*_-=[].?@#$&'
set who         = '%n(`whoami`) has %a %l from %M'
set term        = 'rxvt'
# set tperiod     =  30
set nobeep
set autolist
set color
set colorcat
set listlinks
set addsuffix
set autocorrect
set autoexpand
set printexitvalue
set rmstar
set colorcat
set csubstnonl
set filec
set backslash_quote
set pushdtohome
set noding
set nokanji
set pushdsilent

unset {noclobber,ignoreeof,rprompt,ellipsis,autologout,pushdsilent}
unset {beepcmd,afsuser,ampm,catalog,cdpath,notify,recexact}
unset {recognize_only_executables}

## ENVIRONMENT
## -----------

if ( ! $?HOST ) then
     setenv HOST 'linbox'
endif

setenv MAIL    ${HOME}/mail/
setenv MAILDIR ${MAIL}

# setenv JAVA_HOME /usr/lib/jvm/java-6-sun/jre

setenv PATH       /bin:/usr/bin:/usr/local/bin:/usr/local/pgsql/bin:/usr/games:/usr/X11R6/bin:/usr/NX/bin:${HOME}/bin:/usr/lib/jvm/java-6-sun/bin:/usr/lib/jvm/java-6-sun/jre/bin:/usr/lib/jvm/java-1.5.0-sun/jre/bin/
setenv MANPATH    /usr/share/man:/usr/local/man:/usr/X11R6/man:/usr/share/postgresql/8.3/man
setenv INFOPATH   /usr/share/info:/usr/local/share/info
setenv LOCALEPATH /usr/share/locale
setenv LS_COLORS  'pi=40;33:bd=40;33;01:cd=40;33;01:or=01;05;37;41:mi=01;05;37;41:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.xbm=01;35:*.xpm=01;35:*.png=01;35:*.mng=01;35:*.tif=01;35:*.tiff=01;35:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.rar=01;31:*.bz2=01;31:*.bz=01;31:*.tz=01;31:*.rpm=01;31:*.deb=01;31:*.cpio=01;31:*.7z=01;31:*.svg=01;35:*.xcf=01;35'
setenv PRINTER    'iP1800_series'
setenv LANG       en_GB.UTF-8
setenv LANGUAGE   ${LANG}
setenv LC_ALL     ${LANG}
setenv MACHINE_NAME i686
setenv TERM         rxvt
setenv COLORTERM    rxvt
setenv EDITOR       /usr/bin/vim
setenv VISUAL       ${EDITOR}
setenv PAGER        /usr/bin/less
setenv LESSOPEN     '|gzip -cdfq %s'
setenv CC           colorgcc
setenv BROWSER      /usr/bin/sensible-browser
setenv FTPANONPASS  nobody@nodomain.com
setenv EMAIL        ******@******.***

setenv IRCNAME `whoami`
setenv IRCNICK hex1a4

# setenv JAVA_HOME /usr/lib/jvm/java-6-sun/jre
setenv JAVA_FONTS /usr/share/fonts/truetype
                       
# Xfce
setenv XDG_CONFIG_HOME ${HOME}/.config/
setenv XDG_CACHE_HOME  ${HOME}/.cache/
setenv XDG_DATA_HOME   ${HOME}/.local/share/
setenv XDG_DATA_DIRS   /etc/xdg/xubuntu:/usr/share:/usr/local/share:${HOME}/.local/share
# X
setenv XAUTHORITY ${HOME}/.Xauthority
setenv XNESTSIZE  800x600
# PostgreSQL
setenv LD_LIBRARY_PATH /usr/local/pgsql/lib
setenv PGDATA          /usr/local/pgsql/data
setenv PGBIN           /usr/local/pgsql/bin
setenv PGHOST          ${HOST}
setenv PGPORT          5432
setenv PGUSER          ${USER}

setenv UNZIPCMD unzip

unsetenv {HPATH,MLDONKEY_DIR,MLDONKEY_MESSAGES}

```

---

### Post by geo132 on 2010-12-24
i ran tcsh --version
```
tcsh 6.17.00 (Astron) 2009-07-10 (i486-intel-linux) options wide,nls,dl,al,kan,rh,nd,color,filec

```
is there any way i can get same version as yours?

---

### Post by x1a4 on 2010-12-26
To downgrade tcsh, the best way would be to first remove the tcsh version that's in your version's repos, then download and compile (usually it's quite easy) from here: [ftp://ftp.astron.com/pub/tcsh/old/](ftp://ftp.astron.com/pub/tcsh/old/)

Look in the README file for instructions.  Before building it be sure to look in config_f.h to enable/disable options.  

Another way is to enable Hardy universe repositories and install from there.  

Hardy universe sources are: 
(Replace 'ca.' with your country code or remove if you're in the U.S.)
```

deb http://ca.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy universe
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates universe

```
[COLOR="Red"]**Disable after you're done.  Don't update anything else!**[/COLOR]  Try compiling from source first, as that's the best and safest method.

---

### Post by gmargo on 2010-12-26
> **geo132 said:**
> ]is there any way i can get same version as yours?

It's not a shell bug.  Do not downgrade your **tcsh**.  Fix your script.

The troublesome string is "08" or "09" - the leading zero leads **tcsh** to interpret "08" as an octal number, and "8" is not a valid octal digit, so you get an error.  Note that "07" works.

Obvious solution: strip the leading zero and adjust the checks.

Another problem: Don't read from standard input for your test string.  Use an argument!

Fixed script:
```

#!/bin/tcsh -f
set line = $1
if ( "$line" == "" ) then
    echo "Usage: $0 DD.MM.YY[YY]"
    exit 1
endif

set temp = `echo $line | cut -d"." -f3 | sed 's/^0//' `
#echo $temp

if ($temp >= 0 && $temp < 10) then
    echo 200$temp
else if ($temp >= 10 && $temp < 15) then
    echo 20$temp
else if ($temp >= 15 && $temp <= 99) then
    echo 19$temp
else
    echo $temp
endif

```

---

