---
title: "minor substitution help -vi or bash-"
date: 2009-09-09
forum: General Help
---

### Post by galoluscus on 2009-09-09
Hey there, I am creating / editing a file for work and need to alter the text and am having a minor difficulty. I know the solution is incredibly simple - but I am being exceptionally stupid about it.
 
The file is in the format of:
Brand: size: type: serial:
Amerex 20 abc zf113086
Simplex 20 cg994
Badger 2.5 qw-0882
 
What I want to do is change the 2 lowercase letters in the serial number to UPPERCASE. Some have dashes, others do not. 
Any help would be greatly appreciated.
 
File created in vim. About 200 lines and growing, not all serial numbers have letters in them. It is a Fire Extinguisher database.
 
Thank You for your time.
Good Day to You, Galo.

---

### Post by Brandon Williams on 2009-09-09
Assuming that all alpha characters in the serial should be capitalized, here's a way to do it with bash and tr:
```
cat database | while read line; do
    FIELDS=( $line )
    if [ ${#FIELDS[@] -eq 3 ]; then
        echo ${FIELDS[0]} ${FIELDS[1]} $(echo ${FIELDS[2]} | tr 'a-z' 'A-Z')
    elif [ ${#FIELDS[@]} -eq 4 ] && [ ${FIELDS[0]} != "Brand:" ]; then
        echo ${FIELDS[0]} ${FIELDS[1]} ${FIELDS[2]} $(echo ${FIELDS[3]} | tr 'a-z' 'A-Z')
    else
        echo $line
    fi
done
```

Your sample data includes records with 3 fields and records with 4 fields, so I've tried to handle both cases. That said, you would probably be better off normalizing the data to ensure that all records have the same number of fields.

---

### Post by galoluscus on 2009-09-11
Hey, Thank You Very much.
  This works . 
 I edited the data to only 3 fields for simplicity - and the fact that it is useless info anyway, as they area all the same i.e.  ABC Class fire ext.
 Again, I sincerely appreciate your effort and timely response to this.

  Good Day to You.
  Jason

---

### Post by ghostdog74 on 2009-09-11
> **Brandon Williams said:**
> Assuming that all alpha characters in the serial should be capitalized, here's a way to do it with bash and tr:
```
cat database | while read line; do
    FIELDS=( $line )
    if [ ${#FIELDS[@] -eq 3 ]; then
        echo ${FIELDS[0]} ${FIELDS[1]} $(echo ${FIELDS[2]} | tr 'a-z' 'A-Z')
    elif [ ${#FIELDS[@]} -eq 4 ] && [ ${FIELDS[0]} != "Brand:" ]; then
        echo ${FIELDS[0]} ${FIELDS[1]} ${FIELDS[2]} $(echo ${FIELDS[3]} | tr 'a-z' 'A-Z')
    else
        echo $line
    fi
done
```

Your sample data includes records with 3 fields and records with 4 fields, so I've tried to handle both cases. That said, you would probably be better off normalizing the data to ensure that all records have the same number of fields.

no need to use cat. Also, good effort, BUT, it can be simpler...

---

### Post by falconindy on 2009-09-11
Eh. Way too complex. awk makes short work of this:
```
awk '{print $1 " " $2 " " toupper($3)}' database
```

If it turns out for whatever reason your records **do **need to vary in number of records, you can use this:
```
awk '{ i = 1 while (i < NF) { printf $i " ", i++ } print toupper($NF) }' database
```
That'll just run toupper() on the last record in each line.

---

