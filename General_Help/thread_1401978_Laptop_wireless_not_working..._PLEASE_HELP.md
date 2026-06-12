---
title: "Laptop wireless not working... PLEASE HELP"
date: 2010-02-08
forum: General Help
---

### Post by schwabdale on 2010-02-08
Hello, I just purchased this 
[http://www.bestbuy.com/site/Dell+-+Inspiron+Laptop+with+Intel%26%23174;+Pentium%26%23174;+Processor+-+Ice+Blue/9693473.p?id=1218150608785&skuId=9693473](http://www.bestbuy.com/site/Dell+-+Inspiron+Laptop+with+Intel%26%23174;+Pentium%26%23174;+Processor+-+Ice+Blue/9693473.p?id=1218150608785&skuId=9693473)

However, I have no Idea how to get the wireless card to work. 
Can someone who knows Ubuntu 9.1 please help me get this going?

Thanks in advance

---

### Post by Greenwidth on 2010-02-08
You need to find what chipset is on your card. Type ```
lspci
``` into a terminal and post the output here.

---

### Post by schwabdale on 2010-02-08
intel corporation 82801I (ICH9 Family) PCI Express

sorry, I dont know why I cant copy and paste, do you need any more info?

---

### Post by Greenwidth on 2010-02-08
That's sound.
Try:
```
lspci | grep Net
```

---

