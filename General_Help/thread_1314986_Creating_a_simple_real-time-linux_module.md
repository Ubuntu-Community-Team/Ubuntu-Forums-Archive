---
title: "Creating a simple real-time-linux module"
date: 2009-11-04
forum: General Help
---

### Post by kedarm on 2009-11-04
Hi!

I am trying to create a small (read: hello_world) module, as my first step towards building real-time modules. I am following the steps given [here]("http://www.isd.mel.nist.gov/projects/rtlinux/rtutorial-2.0/doc/basics.htm").

I have written a simple hello_world code -
```
#define __KERNEL__
#define MODULE
#include <linux/kernel.h>
#include <linux/module.h>

int init_module(void)
{
  printk("hello, world!\n"); /* printk = kernel printf, to the console */

  return 0;
}

void cleanup_module(void)
{
  printk("goodbye, world!\n");

  return;
}
```
and try to compile it in the following manner -
```
gcc -c hello_world.c -I /usr/src/linux-source-2.6.28/include/
```

However, I get the following errors (which I have no clue how to decipher :( ) -
> ~/workspace/work/rtl/hello_world$ gcc -c hello_world.c -I /usr/src/linux-source-2.6.28/include/
In file included from /usr/src/linux-source-2.6.28/include/linux/kernel.h:11,
                 from hello_world.c:3:
/usr/src/linux-source-2.6.28/include/linux/linkage.h:5:25: error: asm/linkage.h: No such file or directory
In file included from /usr/src/linux-source-2.6.28/include/linux/kernel.h:15,
                 from hello_world.c:3:
/usr/src/linux-source-2.6.28/include/linux/bitops.h:17:24: error: asm/bitops.h: No such file or directory
In file included from /usr/src/linux-source-2.6.28/include/linux/kernel.h:16,
                 from hello_world.c:3:
/usr/src/linux-source-2.6.28/include/linux/log2.h:52: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘is_power_of_2’
In file included from hello_world.c:3:
/usr/src/linux-source-2.6.28/include/linux/kernel.h:21:21: error: asm/bug.h: No such file or directory
In file included from hello_world.c:3:
/usr/src/linux-source-2.6.28/include/linux/kernel.h:167: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-source-2.6.28/include/linux/kernel.h:168: error: format string argument not a string type
/usr/src/linux-source-2.6.28/include/linux/kernel.h:167: warning: conflicting types for built-in function ‘snprintf’
/usr/src/linux-source-2.6.28/include/linux/kernel.h:169: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-source-2.6.28/include/linux/kernel.h:169: warning: conflicting types for built-in function ‘vsnprintf’
/usr/src/linux-source-2.6.28/include/linux/kernel.h:171: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-source-2.6.28/include/linux/kernel.h:172: error: format string argument not a string type
/usr/src/linux-source-2.6.28/include/linux/kernel.h:173: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-source-2.6.28/include/linux/kernel.h:236: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘printk_timed_ratelimit’
/usr/src/linux-source-2.6.28/include/linux/kernel.h:301: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-source-2.6.28/include/linux/kernel.h:303: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-source-2.6.28/include/linux/kernel.h:303: error: expected declaration specifiers or ‘...’ before ‘bool’
/usr/src/linux-source-2.6.28/include/linux/kernel.h:306: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-source-2.6.28/include/linux/kernel.h:306: error: expected declaration specifiers or ‘...’ before ‘bool’
/usr/src/linux-source-2.6.28/include/linux/kernel.h:308: error: expected declaration specifiers or ‘...’ before ‘size_t’
In file included from /usr/src/linux-source-2.6.28/include/linux/list.h:6,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:9,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/prefetch.h:14:27: error: asm/processor.h: No such file or directory
/usr/src/linux-source-2.6.28/include/linux/prefetch.h:15:23: error: asm/cache.h: No such file or directory
In file included from /usr/src/linux-source-2.6.28/include/linux/list.h:6,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:9,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/prefetch.h:53: error: expected declaration specifiers or ‘...’ before ‘size_t’
In file included from /usr/src/linux-source-2.6.28/include/linux/module.h:9,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/list.h:7:24: error: asm/system.h: No such file or directory
In file included from /usr/src/linux-source-2.6.28/include/linux/preempt.h:9,
                 from /usr/src/linux-source-2.6.28/include/linux/spinlock.h:50,
                 from /usr/src/linux-source-2.6.28/include/linux/seqlock.h:29,
                 from /usr/src/linux-source-2.6.28/include/linux/time.h:8,
                 from /usr/src/linux-source-2.6.28/include/linux/stat.h:60,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:10,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/thread_info.h:34: error: expected specifier-qualifier-list before ‘clockid_t’
In file included from /usr/src/linux-source-2.6.28/include/linux/preempt.h:9,
                 from /usr/src/linux-source-2.6.28/include/linux/spinlock.h:50,
                 from /usr/src/linux-source-2.6.28/include/linux/seqlock.h:29,
                 from /usr/src/linux-source-2.6.28/include/linux/time.h:8,
                 from /usr/src/linux-source-2.6.28/include/linux/stat.h:60,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:10,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/thread_info.h:55:29: error: asm/thread_info.h: No such file or directory
/usr/src/linux-source-2.6.28/include/linux/thread_info.h:64: warning: ‘struct thread_info’ declared inside parameter list
/usr/src/linux-source-2.6.28/include/linux/thread_info.h:64: warning: its scope is only this definition or declaration, which is probably not what you want
/usr/src/linux-source-2.6.28/include/linux/thread_info.h: In function ‘set_ti_thread_flag’:
/usr/src/linux-source-2.6.28/include/linux/thread_info.h:66: error: dereferencing pointer to incomplete type
/usr/src/linux-source-2.6.28/include/linux/thread_info.h: At top level:
/usr/src/linux-source-2.6.28/include/linux/thread_info.h:69: warning: ‘struct thread_info’ declared inside parameter list
/usr/src/linux-source-2.6.28/include/linux/thread_info.h: In function ‘clear_ti_thread_flag’:
/usr/src/linux-source-2.6.28/include/linux/thread_info.h:71: error: dereferencing pointer to incomplete type
/usr/src/linux-source-2.6.28/include/linux/thread_info.h: At top level:
/usr/src/linux-source-2.6.28/include/linux/thread_info.h:74: warning: ‘struct thread_info’ declared inside parameter list
/usr/src/linux-source-2.6.28/include/linux/thread_info.h: In function ‘test_and_set_ti_thread_flag’:
/usr/src/linux-source-2.6.28/include/linux/thread_info.h:76: error: dereferencing pointer to incomplete type
/usr/src/linux-source-2.6.28/include/linux/thread_info.h: At top level:
/usr/src/linux-source-2.6.28/include/linux/thread_info.h:79: warning: ‘struct thread_info’ declared inside parameter list
/usr/src/linux-source-2.6.28/include/linux/thread_info.h: In function ‘test_and_clear_ti_thread_flag’:
/usr/src/linux-source-2.6.28/include/linux/thread_info.h:81: error: dereferencing pointer to incomplete type
/usr/src/linux-source-2.6.28/include/linux/thread_info.h: At top level:
/usr/src/linux-source-2.6.28/include/linux/thread_info.h:84: warning: ‘struct thread_info’ declared inside parameter list
/usr/src/linux-source-2.6.28/include/linux/thread_info.h: In function ‘test_ti_thread_flag’:
/usr/src/linux-source-2.6.28/include/linux/thread_info.h:86: error: dereferencing pointer to incomplete type
In file included from /usr/src/linux-source-2.6.28/include/linux/seqlock.h:29,
                 from /usr/src/linux-source-2.6.28/include/linux/time.h:8,
                 from /usr/src/linux-source-2.6.28/include/linux/stat.h:60,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:10,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/spinlock.h:348:24: error: asm/atomic.h: No such file or directory
In file included from /usr/src/linux-source-2.6.28/include/linux/seqlock.h:29,
                 from /usr/src/linux-source-2.6.28/include/linux/time.h:8,
                 from /usr/src/linux-source-2.6.28/include/linux/stat.h:60,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:10,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/spinlock.h: At top level:
/usr/src/linux-source-2.6.28/include/linux/spinlock.h:357: error: expected ‘)’ before ‘*’ token
In file included from /usr/src/linux-source-2.6.28/include/linux/time.h:9,
                 from /usr/src/linux-source-2.6.28/include/linux/stat.h:60,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:10,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/math64.h:5:23: error: asm/div64.h: No such file or directory
In file included from /usr/src/linux-source-2.6.28/include/linux/stat.h:60,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:10,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/time.h:15: error: expected specifier-qualifier-list before ‘time_t’
/usr/src/linux-source-2.6.28/include/linux/time.h:21: error: expected specifier-qualifier-list before ‘time_t’
/usr/src/linux-source-2.6.28/include/linux/time.h: In function ‘timespec_equal’:
/usr/src/linux-source-2.6.28/include/linux/time.h:48: error: ‘const struct timespec’ has no member named ‘tv_sec’
/usr/src/linux-source-2.6.28/include/linux/time.h:48: error: ‘const struct timespec’ has no member named ‘tv_sec’
/usr/src/linux-source-2.6.28/include/linux/time.h:48: error: ‘const struct timespec’ has no member named ‘tv_nsec’
/usr/src/linux-source-2.6.28/include/linux/time.h:48: error: ‘const struct timespec’ has no member named ‘tv_nsec’
/usr/src/linux-source-2.6.28/include/linux/time.h: In function ‘timespec_compare’:
/usr/src/linux-source-2.6.28/include/linux/time.h:58: error: ‘const struct timespec’ has no member named ‘tv_sec’
/usr/src/linux-source-2.6.28/include/linux/time.h:58: error: ‘const struct timespec’ has no member named ‘tv_sec’
/usr/src/linux-source-2.6.28/include/linux/time.h:60: error: ‘const struct timespec’ has no member named ‘tv_sec’
/usr/src/linux-source-2.6.28/include/linux/time.h:60: error: ‘const struct timespec’ has no member named ‘tv_sec’
/usr/src/linux-source-2.6.28/include/linux/time.h:62: error: ‘const struct timespec’ has no member named ‘tv_nsec’
/usr/src/linux-source-2.6.28/include/linux/time.h:62: error: ‘const struct timespec’ has no member named ‘tv_nsec’
/usr/src/linux-source-2.6.28/include/linux/time.h: In function ‘timeval_compare’:
/usr/src/linux-source-2.6.28/include/linux/time.h:67: error: ‘const struct timeval’ has no member named ‘tv_sec’
/usr/src/linux-source-2.6.28/include/linux/time.h:67: error: ‘const struct timeval’ has no member named ‘tv_sec’
/usr/src/linux-source-2.6.28/include/linux/time.h:69: error: ‘const struct timeval’ has no member named ‘tv_sec’
/usr/src/linux-source-2.6.28/include/linux/time.h:69: error: ‘const struct timeval’ has no member named ‘tv_sec’
/usr/src/linux-source-2.6.28/include/linux/time.h:71: error: ‘const struct timeval’ has no member named ‘tv_usec’
/usr/src/linux-source-2.6.28/include/linux/time.h:71: error: ‘const struct timeval’ has no member named ‘tv_usec’
/usr/src/linux-source-2.6.28/include/linux/time.h: At top level:
/usr/src/linux-source-2.6.28/include/linux/time.h:78: error: expected declaration specifiers or ‘...’ before ‘time_t’
/usr/src/linux-source-2.6.28/include/linux/time.h: In function ‘timespec_sub’:
/usr/src/linux-source-2.6.28/include/linux/time.h:89: error: ‘struct timespec’ has no member named ‘tv_sec’
/usr/src/linux-source-2.6.28/include/linux/time.h:89: error: ‘struct timespec’ has no member named ‘tv_sec’
/usr/src/linux-source-2.6.28/include/linux/time.h:90: error: ‘struct timespec’ has no member named ‘tv_nsec’
/usr/src/linux-source-2.6.28/include/linux/time.h:90: error: ‘struct timespec’ has no member named ‘tv_nsec’
/usr/src/linux-source-2.6.28/include/linux/time.h:90: error: too many arguments to function ‘set_normalized_timespec’
/usr/src/linux-source-2.6.28/include/linux/time.h: In function ‘timespec_to_ns’:
/usr/src/linux-source-2.6.28/include/linux/time.h:148: error: ‘const struct timespec’ has no member named ‘tv_sec’
/usr/src/linux-source-2.6.28/include/linux/time.h:148: error: ‘const struct timespec’ has no member named ‘tv_nsec’
/usr/src/linux-source-2.6.28/include/linux/time.h: In function ‘timeval_to_ns’:
/usr/src/linux-source-2.6.28/include/linux/time.h:160: error: ‘const struct timeval’ has no member named ‘tv_sec’
/usr/src/linux-source-2.6.28/include/linux/time.h:161: error: ‘const struct timeval’ has no member named ‘tv_usec’
/usr/src/linux-source-2.6.28/include/linux/time.h: In function ‘timespec_add_ns’:
/usr/src/linux-source-2.6.28/include/linux/time.h:190: error: ‘struct timespec’ has no member named ‘tv_sec’
/usr/src/linux-source-2.6.28/include/linux/time.h:190: error: ‘struct timespec’ has no member named ‘tv_nsec’
/usr/src/linux-source-2.6.28/include/linux/time.h:191: error: ‘struct timespec’ has no member named ‘tv_nsec’
In file included from /usr/src/linux-source-2.6.28/include/linux/module.h:10,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/stat.h: At top level:
/usr/src/linux-source-2.6.28/include/linux/stat.h:64: error: expected specifier-qualifier-list before ‘dev_t’
In file included from /usr/src/linux-source-2.6.28/include/linux/mmzone.h:9,
                 from /usr/src/linux-source-2.6.28/include/linux/gfp.h:4,
                 from /usr/src/linux-source-2.6.28/include/linux/kmod.h:22,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:13,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/wait.h:26:25: error: asm/current.h: No such file or directory
In file included from /usr/src/linux-source-2.6.28/include/linux/bitmap.h:8,
                 from /usr/src/linux-source-2.6.28/include/linux/nodemask.h:89,
                 from /usr/src/linux-source-2.6.28/include/linux/mmzone.h:16,
                 from /usr/src/linux-source-2.6.28/include/linux/gfp.h:4,
                 from /usr/src/linux-source-2.6.28/include/linux/kmod.h:22,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:13,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/string.h:19:24: error: asm/string.h: No such file or directory
In file included from /usr/src/linux-source-2.6.28/include/linux/bitmap.h:8,
                 from /usr/src/linux-source-2.6.28/include/linux/nodemask.h:89,
                 from /usr/src/linux-source-2.6.28/include/linux/mmzone.h:16,
                 from /usr/src/linux-source-2.6.28/include/linux/gfp.h:4,
                 from /usr/src/linux-source-2.6.28/include/linux/kmod.h:22,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:13,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/string.h:28: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘strlcpy’
/usr/src/linux-source-2.6.28/include/linux/string.h:37: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘strlcat’
/usr/src/linux-source-2.6.28/include/linux/string.h:52: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-source-2.6.28/include/linux/string.h:52: warning: conflicting types for built-in function ‘strncasecmp’
/usr/src/linux-source-2.6.28/include/linux/string.h:58: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-source-2.6.28/include/linux/string.h:106: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-source-2.6.28/include/linux/string.h:107: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-source-2.6.28/include/linux/string.h:112: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sysfs_streq’
/usr/src/linux-source-2.6.28/include/linux/string.h:114: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘memory_read_from_buffer’
In file included from /usr/src/linux-source-2.6.28/include/linux/nodemask.h:89,
                 from /usr/src/linux-source-2.6.28/include/linux/mmzone.h:16,
                 from /usr/src/linux-source-2.6.28/include/linux/gfp.h:4,
                 from /usr/src/linux-source-2.6.28/include/linux/kmod.h:22,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:13,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/bitmap.h: In function ‘bitmap_zero’:
/usr/src/linux-source-2.6.28/include/linux/bitmap.h:142: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-source-2.6.28/include/linux/bitmap.h:142: error: (Each undeclared identifier is reported only once
/usr/src/linux-source-2.6.28/include/linux/bitmap.h:142: error: for each function it appears in.)
/usr/src/linux-source-2.6.28/include/linux/bitmap.h: In function ‘bitmap_fill’:
/usr/src/linux-source-2.6.28/include/linux/bitmap.h:152: error: ‘size_t’ undeclared (first use in this function)
/usr/src/linux-source-2.6.28/include/linux/bitmap.h:152: error: expected ‘;’ before ‘nlongs’
/usr/src/linux-source-2.6.28/include/linux/bitmap.h:153: error: ‘nlongs’ undeclared (first use in this function)
/usr/src/linux-source-2.6.28/include/linux/bitmap.h:157: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-source-2.6.28/include/linux/bitmap.h: In function ‘bitmap_copy’:
/usr/src/linux-source-2.6.28/include/linux/bitmap.h:163: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-source-2.6.28/include/linux/bitmap.h: In function ‘bitmap_and’:
/usr/src/linux-source-2.6.28/include/linux/bitmap.h:174: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-source-2.6.28/include/linux/bitmap.h: In function ‘bitmap_or’:
/usr/src/linux-source-2.6.28/include/linux/bitmap.h:183: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-source-2.6.28/include/linux/bitmap.h: In function ‘bitmap_xor’:
/usr/src/linux-source-2.6.28/include/linux/bitmap.h:192: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-source-2.6.28/include/linux/bitmap.h: In function ‘bitmap_andnot’:
/usr/src/linux-source-2.6.28/include/linux/bitmap.h:201: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-source-2.6.28/include/linux/bitmap.h: In function ‘bitmap_complement’:
/usr/src/linux-source-2.6.28/include/linux/bitmap.h:210: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-source-2.6.28/include/linux/bitmap.h: In function ‘bitmap_equal’:
/usr/src/linux-source-2.6.28/include/linux/bitmap.h:219: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-source-2.6.28/include/linux/bitmap.h: In function ‘bitmap_intersects’:
/usr/src/linux-source-2.6.28/include/linux/bitmap.h:228: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-source-2.6.28/include/linux/bitmap.h: In function ‘bitmap_subset’:
/usr/src/linux-source-2.6.28/include/linux/bitmap.h:237: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-source-2.6.28/include/linux/bitmap.h: In function ‘bitmap_empty’:
/usr/src/linux-source-2.6.28/include/linux/bitmap.h:245: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-source-2.6.28/include/linux/bitmap.h: In function ‘bitmap_full’:
/usr/src/linux-source-2.6.28/include/linux/bitmap.h:253: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-source-2.6.28/include/linux/bitmap.h: In function ‘bitmap_weight’:
/usr/src/linux-source-2.6.28/include/linux/bitmap.h:261: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-source-2.6.28/include/linux/bitmap.h: In function ‘bitmap_shift_right’:
/usr/src/linux-source-2.6.28/include/linux/bitmap.h:269: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-source-2.6.28/include/linux/bitmap.h: In function ‘bitmap_shift_left’:
/usr/src/linux-source-2.6.28/include/linux/bitmap.h:278: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
In file included from /usr/src/linux-source-2.6.28/include/linux/gfp.h:4,
                 from /usr/src/linux-source-2.6.28/include/linux/kmod.h:22,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:13,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/mmzone.h:18:26: error: linux/bounds.h: No such file or directory
/usr/src/linux-source-2.6.28/include/linux/mmzone.h:20:22: error: asm/page.h: No such file or directory
In file included from /usr/src/linux-source-2.6.28/include/linux/gfp.h:4,
                 from /usr/src/linux-source-2.6.28/include/linux/kmod.h:22,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:13,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/mmzone.h: At top level:
/usr/src/linux-source-2.6.28/include/linux/mmzone.h:277: error: ‘MAX_NR_ZONES’ undeclared here (not in a function)
/usr/src/linux-source-2.6.28/include/linux/mmzone.h:333: error: expected specifier-qualifier-list before ‘atomic_long_t’
In file included from /usr/src/linux-source-2.6.28/include/linux/notifier.h:13,
                 from /usr/src/linux-source-2.6.28/include/linux/memory_hotplug.h:6,
                 from /usr/src/linux-source-2.6.28/include/linux/mmzone.h:640,
                 from /usr/src/linux-source-2.6.28/include/linux/gfp.h:4,
                 from /usr/src/linux-source-2.6.28/include/linux/kmod.h:22,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:13,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/mutex.h:50: error: expected specifier-qualifier-list before ‘atomic_t’
/usr/src/linux-source-2.6.28/include/linux/mutex.h: In function ‘mutex_is_locked’:
/usr/src/linux-source-2.6.28/include/linux/mutex.h:117: error: ‘struct mutex’ has no member named ‘count’
In file included from /usr/src/linux-source-2.6.28/include/linux/notifier.h:14,
                 from /usr/src/linux-source-2.6.28/include/linux/memory_hotplug.h:6,
                 from /usr/src/linux-source-2.6.28/include/linux/mmzone.h:640,
                 from /usr/src/linux-source-2.6.28/include/linux/gfp.h:4,
                 from /usr/src/linux-source-2.6.28/include/linux/kmod.h:22,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:13,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/rwsem.h:22:65: error: asm/rwsem.h: No such file or directory
In file included from /usr/src/linux-source-2.6.28/include/linux/memory_hotplug.h:6,
                 from /usr/src/linux-source-2.6.28/include/linux/mmzone.h:640,
                 from /usr/src/linux-source-2.6.28/include/linux/gfp.h:4,
                 from /usr/src/linux-source-2.6.28/include/linux/kmod.h:22,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:13,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/notifier.h: At top level:
/usr/src/linux-source-2.6.28/include/linux/notifier.h:62: error: field ‘rwsem’ has incomplete type
In file included from /usr/src/linux-source-2.6.28/include/linux/gfp.h:4,
                 from /usr/src/linux-source-2.6.28/include/linux/kmod.h:22,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:13,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/mmzone.h: In function ‘populated_zone’:
/usr/src/linux-source-2.6.28/include/linux/mmzone.h:673: error: ‘struct zone’ has no member named ‘present_pages’
/usr/src/linux-source-2.6.28/include/linux/mmzone.h: In function ‘is_normal’:
/usr/src/linux-source-2.6.28/include/linux/mmzone.h:722: error: ‘struct zone’ has no member named ‘zone_pgdat’
/usr/src/linux-source-2.6.28/include/linux/mmzone.h: At top level:
/usr/src/linux-source-2.6.28/include/linux/mmzone.h:747: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-source-2.6.28/include/linux/mmzone.h:747: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/usr/src/linux-source-2.6.28/include/linux/mmzone.h:750: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-source-2.6.28/include/linux/mmzone.h:750: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/usr/src/linux-source-2.6.28/include/linux/mmzone.h:752: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-source-2.6.28/include/linux/mmzone.h:752: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/usr/src/linux-source-2.6.28/include/linux/mmzone.h:754: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-source-2.6.28/include/linux/mmzone.h:754: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/usr/src/linux-source-2.6.28/include/linux/mmzone.h:756: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-source-2.6.28/include/linux/mmzone.h:756: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/usr/src/linux-source-2.6.28/include/linux/mmzone.h:759: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-source-2.6.28/include/linux/mmzone.h:759: error: expected declaration specifiers or ‘...’ before ‘loff_t’
In file included from /usr/src/linux-source-2.6.28/include/linux/topology.h:30,
                 from /usr/src/linux-source-2.6.28/include/linux/mmzone.h:763,
                 from /usr/src/linux-source-2.6.28/include/linux/gfp.h:4,
                 from /usr/src/linux-source-2.6.28/include/linux/kmod.h:22,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:13,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/cpumask.h:279: error: ‘BITS_PER_LONG’ undeclared here (not in a function)
/usr/src/linux-source-2.6.28/include/linux/cpumask.h:821: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cpumask_equal’
/usr/src/linux-source-2.6.28/include/linux/cpumask.h:833: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cpumask_intersects’
/usr/src/linux-source-2.6.28/include/linux/cpumask.h:856: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cpumask_empty’
/usr/src/linux-source-2.6.28/include/linux/cpumask.h:865: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cpumask_full’
/usr/src/linux-source-2.6.28/include/linux/cpumask.h:972: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cpumask_size’
/usr/src/linux-source-2.6.28/include/linux/cpumask.h:1006: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘alloc_cpumask_var’
/usr/src/linux-source-2.6.28/include/linux/cpumask.h:1039: error: expected declaration specifiers or ‘...’ before ‘bool’
/usr/src/linux-source-2.6.28/include/linux/cpumask.h: In function ‘set_cpu_possible’:
/usr/src/linux-source-2.6.28/include/linux/cpumask.h:1041: error: ‘possible’ undeclared (first use in this function)
/usr/src/linux-source-2.6.28/include/linux/cpumask.h: At top level:
/usr/src/linux-source-2.6.28/include/linux/cpumask.h:1047: error: expected declaration specifiers or ‘...’ before ‘bool’
/usr/src/linux-source-2.6.28/include/linux/cpumask.h: In function ‘set_cpu_present’:
/usr/src/linux-source-2.6.28/include/linux/cpumask.h:1049: error: ‘present’ undeclared (first use in this function)
/usr/src/linux-source-2.6.28/include/linux/cpumask.h: At top level:
/usr/src/linux-source-2.6.28/include/linux/cpumask.h:1055: error: expected declaration specifiers or ‘...’ before ‘bool’
/usr/src/linux-source-2.6.28/include/linux/cpumask.h: In function ‘set_cpu_online’:
/usr/src/linux-source-2.6.28/include/linux/cpumask.h:1057: error: ‘online’ undeclared (first use in this function)
/usr/src/linux-source-2.6.28/include/linux/cpumask.h: At top level:
/usr/src/linux-source-2.6.28/include/linux/cpumask.h:1063: error: expected declaration specifiers or ‘...’ before ‘bool’
/usr/src/linux-source-2.6.28/include/linux/cpumask.h: In function ‘set_cpu_active’:
/usr/src/linux-source-2.6.28/include/linux/cpumask.h:1065: error: ‘active’ undeclared (first use in this function)
In file included from /usr/src/linux-source-2.6.28/include/linux/mmzone.h:763,
                 from /usr/src/linux-source-2.6.28/include/linux/gfp.h:4,
                 from /usr/src/linux-source-2.6.28/include/linux/kmod.h:22,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:13,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/topology.h:34:26: error: asm/topology.h: No such file or directory
In file included from /usr/src/linux-source-2.6.28/include/linux/kmod.h:22,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:13,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/gfp.h: At top level:
/usr/src/linux-source-2.6.28/include/linux/gfp.h:231: error: expected ‘)’ before ‘size’
/usr/src/linux-source-2.6.28/include/linux/gfp.h:232: error: expected declaration specifiers or ‘...’ before ‘size_t’
In file included from /usr/src/linux-source-2.6.28/include/linux/module.h:14,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/elf.h:7:21: error: asm/elf.h: No such file or directory
In file included from /usr/src/linux-source-2.6.28/include/linux/module.h:14,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/elf.h:402: error: expected declaration specifiers or ‘...’ before ‘loff_t’
In file included from /usr/src/linux-source-2.6.28/include/linux/kobject.h:21,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:16,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/sysfs.h:31: error: expected specifier-qualifier-list before ‘mode_t’
/usr/src/linux-source-2.6.28/include/linux/sysfs.h:36: error: expected specifier-qualifier-list before ‘mode_t’
/usr/src/linux-source-2.6.28/include/linux/sysfs.h:67: error: expected specifier-qualifier-list before ‘size_t’
/usr/src/linux-source-2.6.28/include/linux/sysfs.h:78: error: expected specifier-qualifier-list before ‘ssize_t’
/usr/src/linux-source-2.6.28/include/linux/sysfs.h:167: error: expected declaration specifiers or ‘...’ before ‘mode_t’
In file included from /usr/src/linux-source-2.6.28/include/linux/kobject.h:24,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:16,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/kref.h:22: error: expected specifier-qualifier-list before ‘atomic_t’
In file included from /usr/src/linux-source-2.6.28/include/linux/module.h:16,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/kobject.h:126: error: expected specifier-qualifier-list before ‘ssize_t’
/usr/src/linux-source-2.6.28/include/linux/kobject.h:221: error: expected declaration specifiers or ‘...’ before ‘size_t’
In file included from /usr/src/linux-source-2.6.28/include/linux/percpu.h:5,
                 from /usr/src/linux-source-2.6.28/include/linux/rcupdate.h:39,
                 from /usr/src/linux-source-2.6.28/include/linux/tracepoint.h:18,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:19,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/slab.h:87: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-source-2.6.28/include/linux/slab.h:87: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-source-2.6.28/include/linux/slab.h:127: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-source-2.6.28/include/linux/slab.h:128: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-source-2.6.28/include/linux/slab.h:130: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ksize’
In file included from /usr/src/linux-source-2.6.28/include/linux/slab.h:156,
                 from /usr/src/linux-source-2.6.28/include/linux/percpu.h:5,
                 from /usr/src/linux-source-2.6.28/include/linux/rcupdate.h:39,
                 from /usr/src/linux-source-2.6.28/include/linux/tracepoint.h:18,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:19,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/slab_def.h:20: error: expected specifier-qualifier-list before ‘size_t’
/usr/src/linux-source-2.6.28/include/linux/slab_def.h:29: error: expected ‘)’ before ‘size’
/usr/src/linux-source-2.6.28/include/linux/slab_def.h:31: error: expected ‘)’ before ‘size’
In file included from /usr/src/linux-source-2.6.28/include/linux/percpu.h:5,
                 from /usr/src/linux-source-2.6.28/include/linux/rcupdate.h:39,
                 from /usr/src/linux-source-2.6.28/include/linux/tracepoint.h:18,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:19,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/slab.h:210: error: expected ‘)’ before ‘n’
/usr/src/linux-source-2.6.28/include/linux/slab.h:228: error: expected ‘)’ before ‘size’
/usr/src/linux-source-2.6.28/include/linux/slab.h:233: error: expected ‘)’ before ‘size’
/usr/src/linux-source-2.6.28/include/linux/slab.h:303: error: expected ‘)’ before ‘size’
/usr/src/linux-source-2.6.28/include/linux/slab.h:314: error: expected ‘)’ before ‘size’
In file included from /usr/src/linux-source-2.6.28/include/linux/rcupdate.h:39,
                 from /usr/src/linux-source-2.6.28/include/linux/tracepoint.h:18,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:19,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/percpu.h:9:24: error: asm/percpu.h: No such file or directory
In file included from /usr/src/linux-source-2.6.28/include/linux/rcupdate.h:39,
                 from /usr/src/linux-source-2.6.28/include/linux/tracepoint.h:18,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:19,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/percpu.h:91: error: expected ‘)’ before ‘size’
In file included from /usr/src/linux-source-2.6.28/include/linux/rcupdate.h:43,
                 from /usr/src/linux-source-2.6.28/include/linux/tracepoint.h:18,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:19,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/completion.h:86: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘try_wait_for_completion’
/usr/src/linux-source-2.6.28/include/linux/completion.h:87: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘completion_done’
In file included from /usr/src/linux-source-2.6.28/include/linux/rcupdate.h:58,
                 from /usr/src/linux-source-2.6.28/include/linux/tracepoint.h:18,
                 from /usr/src/linux-source-2.6.28/include/linux/module.h:19,
                 from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/rcupreempt.h:51: error: expected declaration specifiers or ‘...’ before ‘rcu_dyntick_sched’
/usr/src/linux-source-2.6.28/include/linux/rcupreempt.h:51: warning: data definition has no type or storage class
/usr/src/linux-source-2.6.28/include/linux/rcupreempt.h: In function ‘rcu_qsctr_inc’:
/usr/src/linux-source-2.6.28/include/linux/rcupreempt.h:55: error: ‘rcu_dyntick_sched’ undeclared (first use in this function)
/usr/src/linux-source-2.6.28/include/linux/rcupreempt.h:55: error: lvalue required as unary ‘&’ operand
In file included from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/module.h:20:23: error: asm/local.h: No such file or directory
/usr/src/linux-source-2.6.28/include/linux/module.h:22:24: error: asm/module.h: No such file or directory
In file included from hello_world.c:4:
/usr/src/linux-source-2.6.28/include/linux/module.h: At top level:
/usr/src/linux-source-2.6.28/include/linux/module.h:50: error: expected specifier-qualifier-list before ‘ssize_t’


I use Ubuntu 9.04. To get the linux/module.h, I installed linux-source-2.6.28 and then extracted the linux-source-2.6.28.tar.bz2 in /usr/src/.

Thanks

---

### Post by wildweathel on 2009-11-04
From that web site: "The demonstrations require            the [RTAI]("http://www.isd.mel.nist.gov/projects/rtlinux/#RTAI") version of real-time Linux."  RTAI is no more.  I have no idea what happened to it, but it looks like that tutorial is from 2001.  Ubuntu runs 2.6-series kernels, which were launched in 2004, three years after that tutorial was written.  *Everything* is different now, and that tutorial won't help you.  Sorry.

---

### Post by kedarm on 2009-11-04
Thanks..

Looks like I will have to either install an older version, or hunt for a new tutorial.

I was hoping some sort of backward compatibility or something :(

---

### Post by shantanuspathak on 2010-02-04
So did you get the tutorial ? Please let me know

---

