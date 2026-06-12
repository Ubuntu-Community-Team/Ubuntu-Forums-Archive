---
title: "How to pass arguments through upstart?"
date: 2010-12-21
forum: General Help
---

### Post by coolaj86 on 2010-12-21
Is it possible to pass arguments through upstart?

I've tried this, but it's not working for me.

```

/etc/init/dummy
console output
script
    echo ${FOO} ${BAR} ${BAZ} ${1} ${2} > /tmp/dummy-debug.log
end

```

```

export FOO="Hello"; BAR="Heya"; BAZ="Howdy" start dummy

```

Is this possible?

---

