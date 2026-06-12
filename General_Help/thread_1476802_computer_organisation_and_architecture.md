---
title: "computer organisation and architecture"
date: 2010-05-08
forum: General Help
---

### Post by funjoke88 on 2010-05-08
add $t0 $zero ,$zero
loop: beq $a1,$zero,finish
add $t0,$t0,$a0 //$t0=$t0+$a0
sub $a1,$a1,1
j loop
finish:addi $t0,$t0,100 //a=b+100
add $v0,$zero
 
write the equivalent c language code snippets as comments.
 
i have tried a bit but i not the answer correct a not 
 
can help on

---

### Post by Elfy on 2010-05-08
Perhaps you could say what it is you have tried and where you think it might have gone wrong.

Looking remarkably like homework - > While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums should not be thought of as a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

---

