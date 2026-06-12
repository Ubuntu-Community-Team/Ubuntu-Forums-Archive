---
title: "Stupid GCC compiler does NOT even support local variable for inline assembly"
date: 2010-07-02
forum: General Help
---

### Post by xuancong on 2010-07-02
Hi,

It's good that GCC support intel inline disassembly syntax, but it cannot even simply address local variables/parameters properly, making itself stupid and essentially useless, look at the following:

int myfunc(float f){
 int x;
 float fa[8];
 asm(".intel_syntax noprefix\n"
  "mov eax, [x]\n"  // compile fail 1
  "movss xmm1,[f]\n"  // compile fail 2
  "fld dword ptr [fa+4]\n" // compile fail 3
  ".att_syntax\n"
 );
}

For compile fail 1, I can resolve using the following stupidly looking AT&T syntax (why stupid: empty instruction field, only preload register value), but it works nonetheless:
""::"a"(x)
though that cannot deal with "mov eax,[x+4]"
For compile fail 2 and 3, I've no idea except resolving to using other registers but apparantly I'm running out of registers in the real application, because I want to translate following Visual C++ code into g++, but it seems not going to work unless I switch all to global variables which will incur massive cache misses,

// Compute posterior for all mixtures
void ComputeGMM( int n_mix, int n_dim, float *pObs,
     float *pMean, float *pDCov,
     float *pGConst,float *pOut ){
 DWORD exp_bias = 127;
 float exp_mul = (float)(-0.5*M_LOG2E);
 float exp_max = 127.999f;
 float exp_min = -126.999f;
 float vout[4];
 /* SSE optimized batch computation
 ESI: c_mix
 EDI: n_dim/4
 */
 __asm{
  // Load exponent multiplier -> xmm7
  movss  xmm7, exp_mul
  unpcklps xmm7, xmm7
  movlhps  xmm7, xmm7
  // Load max exponent -> xmm6
  movss  xmm6, exp_max
  unpcklps xmm6, xmm6
  movlhps  xmm6, xmm6
  // Load min exponent -> xmm5
  movss  xmm5, exp_min
  unpcklps xmm5, xmm5
  movlhps  xmm5, xmm5
  // Load the four exponent bias (DWORD 127) -> xmm4
  movd  xmm4, exp_bias
  unpcklps xmm4, xmm4
  movlhps  xmm4, xmm4
  // Load the four 1 s -> xmm3
  movaps  xmm3, xmm4
  pslld  xmm3, 23
  // Load loop constants
  mov   esi, n_mix
  mov   edi, n_dim
  shr   esi, 2
  mov   ebx, pMean
  mov   edx, pDCov
re2:
  mov   ecx, edi
  mov   eax, pObs
  xorps  xmm2, xmm2
re1:
  movaps  xmm0, [eax]
  subps  xmm0, [ebx]
  add   eax, 16
  mulps  xmm0, xmm0
  add   ebx, 16
  mulps  xmm0, [edx]
  add   edx, 16
  addps  xmm2, xmm0
  loop  re1
  // up to here, dot product results are in xmm2
  // multiply by -0.5*M_LOG2E to convert from e^(-0.5x) to 2^x
  mulps  xmm2, xmm7
  // cast full exponent into range
  maxps  xmm2, xmm5
  minps  xmm2, xmm6
  // extract integer part -> xmm0
  cvtps2dq xmm0, xmm2
  // compute fractional part -> xmm2
  cvtdq2ps xmm1, xmm0
  subps  xmm2, xmm1
  // store fractional part -> vout[4]
  movups  vout, xmm2
  // compute e^(fractional part) -> vout[4]
  fld   dword ptr [vout]
  fld   dword ptr [vout+4]
  fld   dword ptr [vout+8]
  fld   dword ptr [vout+12]
  f2xm1
  fstp  dword ptr [vout+12]
  f2xm1
  fstp  dword ptr [vout+8]
  f2xm1
  fstp  dword ptr [vout+4]
  f2xm1
  fstp  dword ptr [vout]
  // integer exponent add bias 127
  paddd  xmm0, xmm4
  // shift to floating point exponent position
  pslld  xmm0, 23
  // combine(MUL) the 2 exp result -> xmm0, also multiply with GCONST
  mov   ecx, pGConst
  movups  xmm2, vout
  mov   eax, pOut
  movaps  xmm1, [ecx]
  addps  xmm2, xmm3
  add   ecx, 16
  mulps  xmm0, xmm2
  mov   pGConst,ecx
  mulps  xmm0, xmm1
  movaps  [eax], xmm0
  add   eax, 16
  mov   pOut, eax
  dec   esi
  jnz   re2
 }
}

If you have any idea on how to do this, I would appreciate greatly! Also, I hope future versions of GCC can support intel syntax inline assembly better. Thanks!

Best regards,
Wang Xuancong

---

