---
title: "Perl"
date: 2010-05-06
forum: General Help
---

### Post by andrebarradas on 2010-05-06
```


#!/usr/bin/perl -w
use strict;

#Verificar argumentos

if (@ARGV != 1) {die("Precisar de entrar um argumento,sendo ele uma directoria")}

#Verificar se o argumento é directoria

if (!-d $ARGV[0]) {die("O argumento não é directoria");}

#abertura da directoria

opendir(DIR,"$ARGV[0]") || die ("Erro ao abrir directoria");
my @dir = readdir(DIR);
chomp (@dir);
close (DIR);

my $fich;
my $emptyfile;

foreach my $i (@dir){

if ($i eq "."){next;}
if ($i eq ".."){next;}

    if (-f $i){

       $fich++;
        if (-z $i){
          $emptyfile++;
          print "$emptyfile é ficheiro vazio \n";


        }
   }

}

print " Total Ficheiros: $fich  \n  Total FichVazios: $emptyfile \n";


```

The objective of this code is to count the number of files and the number of empty files of the directory that we called as a argument.In the final the terminal will show(for example) this when we write ./totalemptyfiles.pl files/:

Total files:6
Total empty files:2

Where totalemptyfiles.pl is the script(code) and files/ the directory(first and unique argument).
What is wrong in this code?

Best Wishes,

André Barradas

---

### Post by WorMzy on 2010-05-06
I don't know Perl, but I can immediately see a problem with this line

```
if (@ARGV != 1) {die("Precisar de entrar um argumento,sendo ele uma directoria"$
```

The brace and parenthesis aren't closed. e.g. )}.

---

### Post by andrebarradas on 2010-05-06
> **WorMzy said:**
> I don't know Perl, but I can immediately see a problem with this line

```
if (@ARGV != 1) {die("Precisar de entrar um argumento,sendo ele uma directoria"$
```

The brace and parenthesis aren't closed. e.g. )}.

was a error when i did copy.in my program is correct

Someone can help me to solve the problem please

---

### Post by andrebarradas on 2010-05-07
Someone Can Help me please

---

