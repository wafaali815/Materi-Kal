# Materi KAL

## 1. Teori: Sistem Persamaan Linier

## Definisi

Sebuah *persamaan linier* dengan variabel
$x_1, x_2, \dots, x_n$
adalah persamaan yang dapat dituliskan dalam bentuk:

$$a_1x_1 + a_2x_2 + \dots + a_nx_n = b$$

dengan $a_1, a_2, \dots, a_n, b$ adalah bilangan real.

## Sistem Persamaan Linier (SPL)

Merupakan kumpulan dari beberapa persamaan linier yang melibatkan variabel yang sama. Contoh umum untuk 3 variabel:

$$
\begin{cases}
a_{11}x_1 + a_{12}x_2 + a_{13}x_3 = b_1 \\
a_{21}x_1 + a_{22}x_2 + a_{23}x_3 = b_2 \\
a_{31}x_1 + a_{32}x_2 + a_{33}x_3 = b_3
\end{cases}
$$

## Jenis SPL

*   Homogen jika $b = 0$ pada setiap persamaan
*   Tidak homogen jika ada $b \neq 0$

## Tujuan penyelesaian

Mencari nilai variabel $x_1, x_2, \dots, x_n$ yang memenuhi seluruh persamaan.

## 2. Contoh Sistem Persamaan Linier

Misal sistem:
$$
\begin{cases}
2x + y - z = 8 \\
-3x - y + 2z = -11 \\
-2x + y + 2z = -3
\end{cases}
$$

**Contoh gambar geogebra**

<iframe src="https://www.geogebra.org/calculator/pskjq2e3?embed" width="800" height="600" allowfullscreen style="border: 1px solid #e4e4e4;border-radius: 4px;" frameborder="0"></iframe>

Kita selesaikan sistem ini menggunakan **eliminasi Gauss**.

---

## 3. Penyelesaian Eliminasi Gauss

**matriks augmented**

$$
\left[
\begin{array}{ccc|c}
2 & 1 & -1 & 8 \\
-3 & -1 & 2 & -11 \\
-2 & 1 & 2 & -3
\end{array}
\right]
$$

---

Eliminasi baris 2 dan baris 3 dengan baris 1

R2 = R2 + (3/2)R1
R3 = R3 + R1

$$
\left[
\begin{array}{ccc|c}
2 & 1 & -1 & 8 \\
0 & 0.5 & 0.5 & 1 \\
0 & 2 & 1 & 5
\end{array}
\right]
$$

**Langkah 3: Eliminasi baris 3 dengan baris 2**

R3 = R3 - 4R2

$$
\left[
\begin{array}{ccc|c}
2 & 1 & -1 & 8 \\
0 & 0.5 & 0.5 & 1 \\
0 & 0 & -1 & 1
\end{array}
\right]
$$

---

**Langkah 4: Back substitution**

Dari baris 3:

$$-1z = 1 \Rightarrow z = -1$$

Baris 2:

$$0.5y + 0.5(-1) = 1 \Rightarrow y = 3$$

Baris 1:

$$2x + 3 + 1 = 8 \Rightarrow x = 2$$

---

**Hasil akhir**

$$(x, y, z) = (2, 3, -1)$$

**Penyelesaian Python**

**Penyelesaian SPL dengan** `numpy.linalg.solve`

```python
import numpy as np

# Matriks koefisien
A = np.array([
    [2, 1, -1],
    [-3, -1, 2],
    [-2, 1, 2]
], dtype=float)

# Vektor konstanta
b = np.array([8, -11, -3], dtype=float)

# Penyelesaian SPL
x = np.linalg.solve(A, b)

print("Solusi SPL:", x)
```

Output :

```code
Solusi SPL: [ 2.  3. -1.]

```

# Persamaan Linier dan Nonlinier

## A. Persamaan Linier

Persamaan disebut linier dalam variabel
$x_1, x_2, ..., x_n$
jika dapat ditulis dalam bentuk:

```text
a1*x1 + a2*x2 + ... + an*xn = b
```

dengan semua $a_i$ dan $b$ adalah bilangan real, dan **variabel hanya muncul berpangkat 1**, tidak dikalikan sesamanya, tidak dalam fungsi nonlinier (sin, cos, $e^x$, log, dll).

---

**Contoh 1 (Linier)**

Pertimbangkan persamaan:

$$ \sqrt{3}x + \sin(5) = 2z - e^4y $$

Meskipun koefisiennya mengandung $\sqrt{3}$, $\sin(5)$, dan $e^4$, itu tetap **koefisien konstan**, sehingga persamaan ini linier dalam variabel $x, y, z$.

**Bentuk standar:**

Pindahkan semua variabel ke kiri:

```text
√3 * x + e^4 * y - 2 * z = - sin(5)
```

Persamaan ini tidak homogen, karena ruas kanan tidak sama dengan nol.

## B. Persamaan Nonlinier

Sebuah persamaan disebut nonlinier jika:

*   variabel **berpangkat** selain 1 (misal kuadrat),
*   variabel muncul dalam perkalian sesamanya ( $xy$ , $xyz$ , dll),
*   variabel muncul dalam fungsi nonlinier (sin, exp, log, dsb).

---

**Contoh 2 (Nonlinier)**

Persamaan:

$$ x^2 + y^2 = 1 $$

adalah nonlinier karena variabel muncul dalam **pangkat 2**.

---

**Definisi 1.1.3. Sistem persamaan linier.** Sistem **persamaan linier** (atau **sistem linier**) adalah sekumpulan persamaan linier.

Sistem linier **homogen** adalah sekumpulan persamaan linier homogen.

Saat menampilkan sistem $m$ persamaan dalam $n$ Tidak diketahui $x_1, x_2, \dots x_n$, Kami biasanya menulis setiap persamaan dalam bentuk standar dan menyelaraskan istilah yang sesuai dari setiap persamaan ke dalam kolom:

$$
\begin{array}{rcl}
a_{11}x_1 & + \quad a_{12}x_2 & + \dots + \quad a_{1n}x_n \quad = \quad b_1 \\
a_{21}x_1 & + \quad a_{22}x_2 & + \dots + \quad a_{2n}x_n \quad = \quad b_2 \\
& \vdots \quad \quad \quad \vdots & \quad \quad \quad \quad \quad \vdots \\
a_{m1}x_1 & + \quad a_{m2}x_2 & + \dots + \quad a_{mn}x_n \quad = \quad b_m
\end{array}
$$

Sistem homogen dengan demikian biasanya ditulis sebagai:

$$
\begin{array}{rcl}
a_{11}x_1 & + \quad a_{12}x_2 & + \dots + \quad a_{1n}x_n \quad = \quad 0 \\
a_{21}x_1 & + \quad a_{22}x_2 & + \dots + \quad a_{2n}x_n \quad = \quad 0 \\
& \vdots \quad \quad \quad \vdots & \quad \quad \quad \quad \quad \vdots \\
a_{m1}x_1 & + \quad a_{m2}x_2 & + \dots + \quad a_{mn}x_n \quad = \quad 0
\end{array}
$$