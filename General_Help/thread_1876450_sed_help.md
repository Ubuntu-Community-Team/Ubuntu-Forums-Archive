---
title: "sed help"
date: 2011-11-06
forum: General Help
---

### Post by staticd on 2011-11-06
```

$ echo 'asdasd       cvbcvb'|sed -e 's/[:space:]/,/g'
,,d,,d       ,vb,vb
$echo 'asdasd       cvbcvb'|sed 's/ +/,/g'
asdasd       cvbcvb
$echo 'asdasd       cvbcvb'|sed -n 's/[ ]*//p'
asdasd       cvbcvb

```I want to able to match multiple spaces and replace them with a comma.

```

$echo 'asdasd       cvbcvb'|sed 'magic'
asdasd,cvbcvb

```I'm running oneiric x64.

Thanks

---

### Post by staticd on 2011-11-06
```

sed '/ \{1,\}/,/g'

```

---

### Post by DaithiF on 2011-12-07
any of these:
```
sed 's/ \+/,/g'
sed -r 's/ +/,/g'
sed 's/[[:space:]]\+/,/g'
sed -r 's/[[:space:]]+/,/g'

```

---

