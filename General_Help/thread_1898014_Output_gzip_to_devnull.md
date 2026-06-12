---
title: "Output gzip to dev/null?"
date: 2011-12-20
forum: General Help
---

### Post by Kdar on 2011-12-20
How do I not write output of gzip?

gzip -c file > /dev/null
 

Should this work?

---

### Post by philinux on 2011-12-20
Moved to General Help.

---

### Post by undecim on 2011-12-20
That would do it... Though why would you want to? For a primitive benchmark?

---

### Post by Kdar on 2012-03-16
What actually happens in background with dev/null?

Are output bits still written somewhere? to a buffer or?

---

### Post by codemaniac on 2012-03-16
/dev/null is sometimes called bit bucket or better blackhole .Once something goes into it , could never come out , even light . :D
It discards all the data , any process or program writes on it .

---

### Post by matt_symes on 2012-03-16
Hi

> What actually happens in background with dev/null?

Are output bits still written somewhere? to a buffer or?

Can you read C code ? If you can, look in the kernel sources 

```
/drivers/char/mem.c
```

You will see this struct that handles /dev/null

```
static const struct file_operations null_fops = {
        .llseek         = null_lseek,
        .read           = read_null,
        .write          = write_null,
        .splice_write   = splice_write_null,
};
```

The write operation just returns the number of bytes in the buffer passed to it.

```
static ssize_t write_null(struct file *file, const char __user *buf,
                          size_t count, loff_t *ppos)
{
        return count;
}
```

Nothing is done with the data in the buffer passed to it.

Kind regards

---

