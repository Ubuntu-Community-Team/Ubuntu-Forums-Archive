---
title: "redirecting output of openssl"
date: 2009-07-10
forum: General Help
---

### Post by inanutshellus on 2009-07-10
Short version: I have an encrypted bash file and I'd like to decrypt the contents and run them without making a decrypted file. Really the question is about linux-skills not openssl, and I'm apparently lacking. 

Can it be done?

Long version:

Make a file named "encryptme.sh", like so:
```

 echo "Hello world!"
 export testing="It worked!"

```

encrypt it:

```

 $ openssl enc -aes-256-cbc -salt -in encryptme.sh -out encrypted.sh

```

At this point you can decrypt it as a file with the -d operator:

```

 $ openssl enc -d -aes-256-cbc -in encrypted.sh -out encryptme.sh

```

You can have the decrypted text dump straight to the screen by leaving off -out:

```

 $ openssl enc -d -aes-256-cbc -in encrypted.sh

```

You can even execute it in place with: 

```

 $ openssl enc -d -aes-256-cbc -in encrypted.sh | /bin/bash

```

but that executes it within another bash session, not yours, so if you try to access "$testing" it doesn't work:


```

 $ openssl enc -d -aes-256-cbc -in encrypted.sh | /bin/bash
 enter aes-256-cbc decryption password:
 Hello world!
 $ echo $testing
 $

```

---

### Post by slugmax on 2009-07-10
If you just put the export= line in the encrypted file, this will work:

```

eval $(openssl enc -d -aes-256-cbc -in encrypted.sh)

```

Since eval won't spawn a subshell.

But once you put multiple lines in encrypted.sh, eval bunches them up into one argument and you don't get what you expect.

You can try looping through each line of the decrypted file:

```

while read line; do eval $line; done < "decrypted.sh"

```

This works, but I'm not sure you can decrypt on the fly and still pass
the output into the while loop with this. But maybe it gives you a
starting point.

Doug

---

### Post by inanutshellus on 2009-07-10
I've tried all sorts of crap now and no luck so far. 

Maybe it's not possible, due to the fact that I have to specify a password?

```

 $ while read line; do eval $line; done < openssl enc -d -aes-256-cbc -in encrypted.sh
bash: syntax error near unexpected token `enc'

 $ while read line; do eval $line; done < (openssl enc -d -aes-256-cbc -in encrypted.sh)
bash: syntax error near unexpected token `('

 $ while read line; do eval $line; done < $(openssl enc -d -aes-256-cbc -in encrypted.sh)
enter aes-256-cbc decryption password:   <<<<<===----- Asking twice, for some reason
enter aes-256-cbc decryption password:
bash: $(openssl enc -d -aes-256-cbc -in encrypted.sh): ambiguous redirect

 $ while read line; do eval $line; done < `openssl enc -d -aes-256-cbc -in encrypted.sh`
enter aes-256-cbc decryption password:   <<<<<===----- Asking twice, for some reason
enter aes-256-cbc decryption password:
bash: `openssl enc -d -aes-256-cbc -in encrypted.sh`: ambiguous redirect

 $ while read line; do eval $line; done <& `openssl enc -d -aes-256-cbc -in encrypted.sh`
enter aes-256-cbc decryption password:   <<<<<===----- Asking twice, for some reason
enter aes-256-cbc decryption password:
bash: `openssl enc -d -aes-256-cbc -in encrypted.sh`: ambiguous redirect

 $ while read line; do eval $line; done <& $(`openssl enc -d -aes-256-cbc -in encrypted.sh`)
enter aes-256-cbc decryption password:   <<<<<===----- Asking twice, for some reason
enter aes-256-cbc decryption password:
bash: $(`openssl enc -d -aes-256-cbc -in encrypted.sh`): ambiguous redirect

 $ while read line; do eval $line; done <& openssl enc -d -aes-256-cbc -in encrypted.sh
bash: syntax error near unexpected token `enc'

 $ while read line; do eval $line; done <& "openssl enc -d -aes-256-cbc -in encrypted.sh"
bash: openssl enc -d -aes-256-cbc -in encrypted.sh: ambiguous redirect

 $ while read line; do eval $line; done <& 'openssl enc -d -aes-256-cbc -in encrypted.sh'
bash: openssl enc -d -aes-256-cbc -in encrypted.sh: ambiguous redirect

 $ $(openssl enc -d -aes-256-cbc -in encrypted.sh)
enter aes-256-cbc decryption password:
"Hello world!" export testing="It worked!" <<<<<===----- One line...

 $ `openssl enc -d -aes-256-cbc -in encrypted.sh`
enter aes-256-cbc decryption password:
"Hello world!" export testing="It worked!" <<<<<===----- One line...

```

---

