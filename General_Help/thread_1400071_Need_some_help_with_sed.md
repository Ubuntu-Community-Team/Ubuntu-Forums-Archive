---
title: "Need some help with sed"
date: 2010-02-06
forum: General Help
---

### Post by ecron on 2010-02-06
Hello all,

I've been trying to use sed and the advanced regular expressions to filter and reformat a text file.

ORIGINAL FILE
```

PIXEL := {
	rgbBlue := { uint1;
                 description:="blue color value";
                 name:="blue";}
                 
	rgbGreen := { uint1;
                  description:="green color value";
                  name:="green";}
                  
	rgbRed := { uint1;	
    			description:="red color value";
                name:="red";}
};

```

SED COMMAND
```

sed -r 's/(name|description|permissible|common):=[^;]*(;)//;'

```

RESULT
```

PIXEL := {
	rgbBlue := { uint1;
                 
                 }
                 
	rgbGreen := { uint1;
                  
                  }
                  
	rgbRed := { uint1;	
    			
                }
};

```

DESIRED RESULT
```

PIXEL := {
	rgbBlue := uint1;
	rgbGreen := uint1;
	rgbRed := uint1;
};

```

Now, with the desired result, it is not necessary to get rid of the spacing, but that just makes it easier to read.

I've been having trouble removing the curly brackets on either side of one of the assignment statements, because, it will also filter out the brackets on the PIXEL declaration.

Suggestions? Maybe I need to use another utility?

Thanks all

---

### Post by gmargo on 2010-02-06
Wow, you are truly heroic for attempting to use sed.  I would use perl, but here is a sed solution.  A four stage pipeline starting from your first command which yields your desired output:

```

sed -r 's/(name|description|permissible|common):=[^;]*(;)//;'  | \
sed -r 's/([[:alpha:]] := )\{ ([[:alpha:]])/\1\2/;'            | \
sed -r 's/[[:space:]]+\}[[:space:]]*$//;'                      | \
sed -r '/^[[:space:]]*$/ d;'

```

---

### Post by diesch on 2010-02-06
```
sed -r -e'/(name|description|permissible|common):=[^;]*(;)/d' -e's/\{ uint1;/uint1;/' -e'/^\s*$/d'
```

---

### Post by ratcheer on 2010-02-06
> **gmargo said:**
> wow, you are truly heroic for attempting to use sed.  I would use perl...

+1

---

### Post by ecron on 2010-02-06
Not heroic, just ignorant. I haven't had the oppurtunity to work with perl so I was unaware it was even an option.

And thank you gmargo and diesch, that did the trick.

---

