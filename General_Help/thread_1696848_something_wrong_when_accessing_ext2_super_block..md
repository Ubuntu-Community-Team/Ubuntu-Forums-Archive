---
title: "something wrong when accessing ext2_super_block."
date: 2011-02-28
forum: General Help
---

### Post by sm01718 on 2011-02-28
I used the codes to access ext2_super_block..but there were something wrong when compiling.


cabd@cabd-laptop:~/prog$ gcc -o superb superb.c
In file included from superb.c:1:
/usr/include/linux/ext2_fs.h: In function ‘ext2_mask_flags’:
/usr/include/linux/ext2_fs.h:182: error: ‘FS_DIRSYNC_FL’ undeclared (first use in this function)
/usr/include/linux/ext2_fs.h:182: error: (Each undeclared identifier is reported only once
/usr/include/linux/ext2_fs.h:182: error: for each function it appears in.)
/usr/include/linux/ext2_fs.h:182: error: ‘FS_TOPDIR_FL’ undeclared (first use in this function)
/usr/include/linux/ext2_fs.h:184: error: ‘FS_NODUMP_FL’ undeclared (first use in this function)
/usr/include/linux/ext2_fs.h:184: error: ‘FS_NOATIME_FL’ undeclared (first use in this function)




**here is codes**

  1 #include<linux/ext2_fs.h>
  2 #include<linux/fs.h>
  3 #include<sys/types.h>
  4 #include<sys/stat.h>
  5 #include<stdio.h>
  6 #include<unistd.h>
  7 #include<fcntl.h>
  8 #include<stdlib.h>
  9 #include<string.h>
 10 
 11 #define boot_block_size 1024
 12 
 13 int main()
 14 {
 15         char *buff = (char *)malloc(sizeof(struct ext2_super_block));
 16         int fd = open("/mnt/tmp_mnt",O_RDONLY);
 17         struct ext2_super_block *sblock = (struct ext2_super_block *)malloc(sizeof(struct ext2_super_block));
 18         lseek(fd,boot_block_size,SEEK_CUR);
 19         read(fd,buff,sizeof(struct ext2_super_block));
 20         memcpy((void *)sblock,(void *)buff,sizeof(struct ext2_super_block));
 21         printf("\nmagic number:%u\n",sblock->s_magic);
 22 
 23         close(fd);
 24         return 0;
 25 }

---

### Post by sm01718 on 2011-02-28
I am so sorry for my bad english...:redface::redface:

---

