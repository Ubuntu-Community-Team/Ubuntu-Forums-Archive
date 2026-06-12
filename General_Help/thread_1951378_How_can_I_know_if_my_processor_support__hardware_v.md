---
title: "How can I know if my processor support  hardware virtualization"
date: 2012-04-02
forum: General Help
---

### Post by forsubhi on 2012-04-02
I want to know if my processor support hardware virtualization cos I want to use 64 bit guest system with virtual box.

---

### Post by Dangertux on 2012-04-02
Intel processors 

```

grep vmx /cat/procinfo

```

AMD Processors

```

grep svm /cat/procinfo

```Note : you may need to enable virtualization extensions in your bios, many manufacturers do not enable them by default.

---

### Post by jerrrys on 2012-04-02
Your looking for something like this in BIOS:

[ATTACH]215339[/ATTACH]

And I think vBox will run in just about anything.  If you want to know if you can run [KVM]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=kvm&sa=Search&cof=FORID:9"); open a terminal and enter:
[B]
kvm-ok
[/B]

---

### Post by forsubhi on 2012-04-03
thank you very much

---

