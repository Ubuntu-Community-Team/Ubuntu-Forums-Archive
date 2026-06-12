---
title: "GMP problem"
date: 2010-04-05
forum: General Help
---

### Post by Tapas Bose, India on 2010-04-05
Hello. I installed gmp library. But I getting too much error while compiling program that includes gmp.h. This is my code :
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <gmp.h>
#include <time.h>

#define COMPOSITE        0
#define PROBABLE_PRIME   1

int miller_rabin_pass(mpz_t a, mpz_t n) {
    int i, s, result;
    mpz_t a_to_power, d, n_minus_one;

    mpz_init(n_minus_one);
    mpz_sub_ui(n_minus_one, n, 1);

    s = 0;
    mpz_init_set(d, n_minus_one);
    while (mpz_even_p(d)) {
        mpz_fdiv_q_2exp(d, d, 1);
        s++;
    }

    mpz_init(a_to_power);
    mpz_powm(a_to_power, a, d, n);
    if (mpz_cmp_ui(a_to_power, 1) == 0)  {
        result=PROBABLE_PRIME; goto exit;
    }
    
    for(i=0; i < s-1; i++) {
        if (mpz_cmp(a_to_power, n_minus_one) == 0) {
            result=PROBABLE_PRIME; goto exit;
        }
    
        mpz_powm_ui (a_to_power, a_to_power, 2, n);
    }
    
    if (mpz_cmp(a_to_power, n_minus_one) == 0) {
        result=PROBABLE_PRIME; goto exit;
    }
    
    result = COMPOSITE;

    exit:
        mpz_clear(a_to_power);
        mpz_clear(d);
        mpz_clear(n_minus_one);
    
        return result;
}

int miller_rabin(mpz_t n, gmp_randstate_t rand_state) {
    mpz_t a;
    int repeat;
    mpz_init(a);
    
    for(repeat=0; repeat<20; repeat++) {
        do {
                mpz_urandomm(a, rand_state, n);
        } while (mpz_sgn(a) == 0);
    
        if (miller_rabin_pass(a, n) == COMPOSITE) {
                return COMPOSITE;
        }
    }

    return PROBABLE_PRIME;
}

int main(int argc, char* argv[]) {
    mpz_t n, max, two, p;
    gmp_randstate_t rand_state;
    gmp_randinit_default(rand_state);
    gmp_randseed_ui (rand_state, time(NULL));

    if (strcmp(argv[1], "test") == 0) {
        mpz_init_set_str(n, argv[2], 10);
        puts(miller_rabin(n, rand_state) == PROBABLE_PRIME ? "PRIME" : "COMPOSITE");
    } 
    else if (strcmp(argv[1], "genprime") == 0) {
        mpz_init(max);
        mpz_init_set_ui(two, 2);
        mpz_mul_2exp(max, two, atoi(argv[2])+1);
        mpz_init(p);
    
        do {
                mpz_urandomm(p, rand_state, max);

                if (mpz_even_p(p)) continue;
            if (mpz_fdiv_ui(p, 3) == 0) continue;
            if (mpz_fdiv_ui(p, 5) == 0) continue;
            if (mpz_fdiv_ui(p, 7) == 0) continue;

        } while (miller_rabin(p, rand_state) == COMPOSITE);
        
        mpz_out_str(stdout, 10, p);
        puts("");
    }
    
    return 0;
}
```And I am compiling it with the command:
```
g++ miller_rabin.c -o miller_rabin.o

```The output I am getting :
```
tapas@My-Child:~/Programming/Prime Number Program/Miller - Rabin$ g++ miller_rabin.c -o miller_rabin.o
/tmp/cccwecaW.o: In function `miller_rabin_pass(__mpz_struct*, __mpz_struct*)':
miller_rabin.c:(.text+0xd): undefined reference to `__gmpz_init'
miller_rabin.c:(.text+0x27): undefined reference to `__gmpz_sub_ui'
miller_rabin.c:(.text+0x40): undefined reference to `__gmpz_init_set'
miller_rabin.c:(.text+0x5c): undefined reference to `__gmpz_fdiv_q_2exp'
miller_rabin.c:(.text+0x86): undefined reference to `__gmpz_init'
miller_rabin.c:(.text+0xa6): undefined reference to `__gmpz_powm'
miller_rabin.c:(.text+0xb9): undefined reference to `__gmpz_cmp_ui'
miller_rabin.c:(.text+0xe4): undefined reference to `__gmpz_cmp'
miller_rabin.c:(.text+0x112): undefined reference to `__gmpz_powm_ui'
miller_rabin.c:(.text+0x138): undefined reference to `__gmpz_cmp'
miller_rabin.c:(.text+0x157): undefined reference to `__gmpz_clear'
miller_rabin.c:(.text+0x162): undefined reference to `__gmpz_clear'
miller_rabin.c:(.text+0x16d): undefined reference to `__gmpz_clear'
/tmp/cccwecaW.o: In function `miller_rabin(__mpz_struct*, __gmp_randstate_struct*)':
miller_rabin.c:(.text+0x183): undefined reference to `__gmpz_init'
miller_rabin.c:(.text+0x1a5): undefined reference to `__gmpz_urandomm'
/tmp/cccwecaW.o: In function `main':
miller_rabin.c:(.text+0x210): undefined reference to `__gmp_randinit_default'
miller_rabin.c:(.text+0x22c): undefined reference to `__gmp_randseed_ui'
miller_rabin.c:(.text+0x268): undefined reference to `__gmpz_init_set_str'
miller_rabin.c:(.text+0x2c6): undefined reference to `__gmpz_init'
miller_rabin.c:(.text+0x2da): undefined reference to `__gmpz_init_set_ui'
miller_rabin.c:(.text+0x305): undefined reference to `__gmpz_mul_2exp'
miller_rabin.c:(.text+0x311): undefined reference to `__gmpz_init'
miller_rabin.c:(.text+0x32d): undefined reference to `__gmpz_urandomm'
miller_rabin.c:(.text+0x359): undefined reference to `__gmpz_fdiv_ui'
miller_rabin.c:(.text+0x371): undefined reference to `__gmpz_fdiv_ui'
miller_rabin.c:(.text+0x389): undefined reference to `__gmpz_fdiv_ui'
miller_rabin.c:(.text+0x3d2): undefined reference to `__gmpz_out_str'
collect2: ld returned 1 exit status

```Please help.

---

### Post by Tapas Bose, India on 2010-04-05
This is the proper command :
```
g++ miller_rabin.c -o miller_rabin.o -L/gmp_install/lib -lgmp
```

---

