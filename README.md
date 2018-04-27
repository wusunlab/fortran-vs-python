# A Cheatsheet for Fortran 2008 Syntax: Comparison with Python 3

Wu Sun

Last updated: 2018-04-25

This is a simple cheatsheet to aid scientific programmers who work at the
interfaces of both languages. ***It is by no means an exhaustive list***. (I
have yet to explore some advanced features in the Fortran 2008 standard.)

Make Fortran Modern Again!

This work is licensed under the [Creative Commons Attribution 4.0 International
License.](http://creativecommons.org/licenses/by/4.0/).

<table>
    <tr>
        <td></td>
        <td>Fortran 2008</td>
        <td>Python 3</td>
    </tr>
    <tr>
        <td>Top-level constructs</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>the main program</td>
        <td>
<pre lang="fortran">
program my_program
    ...
end program
</pre>
        </td>
        <td>Not required. Use <code>__main__()</code> if needed.</td>
    </tr>
    <tr>
        <td>modules</td>
        <td>
<pre lang="fortran">
module my_module
    ...
end module my_module
</pre>
        </td>
        <td>A source file is a module.</td>
    </tr>
    <tr>
        <td>subroutines</td>
        <td>
<pre lang="fortran">
subroutine my_subroutine
    ...
end subroutine my_subroutine
</pre>
        </td>
        <td>Functions that have side effects.</td>
    </tr>
    <tr>
        <td>functions</td>
        <td>
<pre lang="fortran">
function f(x) result(res)
    res = ...
end function f
</pre>
        </td>
        <td>
<pre lang="python">
def my_function(x):
    ...
    return res
</pre>
        </td>
    </tr>
    <tr>
        <td>submodules</td>
        <td>
<pre lang="fortran">
module main_module
    ...
contains
&lt;<i>submodule statements</i>&gt;
end module main_module
</pre>
        </td>
        <td>Use folders, <code>__init__.py</code>, and <code>import</code> statement to manage submodules.</td>
    </tr>
    <tr>
        <td>import statement</td>
        <td>
<pre lang="fortran">
use my_module
use my_module, only : fun1, var1
use my_module, only : new_var => var
</pre>
        </td>
        <td>
<pre lang="python">
from my_module import *
from my_module import fun1, var1
from my_module import var as new_var
</pre>
        </td>
    </tr>
    <tr>
        <td>call subroutines and functions</td>
        <td>
<pre lang="fortran">
call my_subroutine(<i>args</i>)
my_function(<i>args</i>)
</pre>
        </td>
        <td>
<pre lang="python">
my_function(<i>args</i>)
</pre>
        </td>
    </tr>
    <tr>
        <td>abort a program</td>
        <td>
<pre lang="fortran">
stop
</pre>
        </td>
        <td>
<pre lang="python">
exit()
</pre>
        </td>
    </tr>
    <tr>
        <td>inline comments</td>
        <td>
<pre lang="fortran">
! This is a comment
</pre>
        </td>
        <td>
<pre lang="python">
# This is a comment
</pre>
        </td>
    </tr>
    <tr>
        <td>line continuation</td>
        <td><code>&</code></td>
        <td><code>\</code></td>
    </tr>
    <tr>
        <td>include external source files</td>
        <td>
<pre lang="fortran">
include <i>'source_file_name'</i>
</pre>
        </td>
        <td>Not supported. Use module import.</td>
    </tr>
    <tr>
        <td>Control flow patterns</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td><code>if</code> construct</td>
        <td>
<pre lang="fortran">
if <i>&lt;logical expr&gt;</i> then
    ...
else if <i>&lt;logical expr&gt;</i> then
    ...
else
    ...
end if
</pre>
        </td>
        <td>
<pre lang="python">
if <i>&lt;logical expr&gt;</i>:
    ...
elif <i>&lt;logical expr&gt;</i>:
    ...
else:
    ...
</pre>
        </td>
    </tr>
    <tr>
        <td><code>case</code> construct</td>
        <td>
<pre lang="fortran">
select case <i>&lt;expr&gt;</i>
    case <i>&lt;value&gt;</i>
        ...
    case <i>&lt;value&gt;</i>
        ...
    case default
        ...
end select
</pre>
        </td>
        <td>Not supported. Any <code>case ... switch</code> statement can be written as an equivalent <code>if-then-else</code> statement.</td>
    </tr>
    <tr>
        <td><code>do</code> construct</td>
        <td>
<pre lang="fortran">
do <i>start_value</i>, <i>end_value</i>, <i>step</i>
    ...
end do
</pre>
        </td>
        <td>
<pre lang="python">
for i in range(start, end, step):
    ...
</pre>
        </td>
    </tr>
    <tr>
        <td><code>do while</code> construct</td>
        <td>
<pre lang="fortran">
do while <i>&lt;logical expr&gt;</i>
    ...
end do
</pre>
        </td>
        <td>
<pre lang="python">
while <i>&lt;logical expr&gt;</i>:
    ...
</pre>
        </td>
    </tr>
    <tr>
        <td>break from a loop</td>
        <td>
<pre lang="fortran">
exit
</pre>
        </td>
        <td>
<pre lang="python">
break
</pre>
        </td>
    </tr>
    <tr>
        <td>leave this iteration and continue to the next iteration</td>
        <td>
<pre lang="fortran">
cycle
</pre>
        </td>
        <td>
<pre lang="python">
continue
</pre>
        </td>
    </tr>
    <tr>
        <td>Data types</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>declaration</td>
        <td>
<pre lang="fortran">
integer(kind=kind_number) :: n = 0
real(kind=kind_number) :: x = 0.
</pre>
        </td>
        <td>
<pre lang="python">
n = 0
x = 0.
</pre>
        </td>
    </tr>
    <tr>
        <td>named constants</td>
        <td>
<pre lang="fortran">
integer, parameter :: answer = 42
real(8), parameter :: pi = 4d0 * atan(1d0)
</pre>
        </td>
        <td>Not supported in Python. Names are <i>bindings</i>.</td>
    </tr>
    <tr>
        <td>complex number</td>
        <td>
<pre lang="fortran">
complex :: z = (1., -1.)
</pre>
        </td>
        <td>
<pre lang="python">
z = 1 - 1j
</pre>
        </td>
    </tr>
    <tr>
        <td>string</td>
        <td>
<pre lang="fortran">
character(len=10) :: str_fixed_length
character(len=:), allocatable :: str_var_length
</pre>
        </td>
        <td>
<pre lang="python">
string = 'this is a string'
</pre>
        </td>
    </tr>
    <tr>
        <td>pointer</td>
        <td>
<pre lang="fortran">
real, pointer :: p
real, target :: r
p => r
</pre>
        </td>
        <td>No built-in support. May invoke from Python C API.<br>(Why would you need it in Python anyway?)</td>
    </tr>
    <tr>
        <td>boolean</td>
        <td>
<pre lang="fortran">
.true.
.false.
</pre>
        </td>
        <td>
<pre lang="python">
True
False
</pre>
        </td>
    </tr>
    <tr>
        <td>logical operators</td>
        <td>
<pre lang="fortran">
.not.
.and.
.or.
.eqv.
.neqv.
</pre>
        </td>
        <td>
<pre lang="python">
not
and
or
</pre>
Other logical operators do not have built-in support.
        </td>
    </tr>
    <tr>
        <td>equal to</td>
        <td>
<pre lang="fortran">
==, .eq.
</pre>
        </td>
        <td>
<pre lang="python">
==
</pre>
        </td>
    </tr>
    <tr>
        <td>not equal to</td>
        <td>
<pre lang="fortran">
/=, .ne.
</pre>
        </td>
        <td>
<pre lang="python">
!=
</pre>
Note: <code>&lt;&gt;</code> is deprecated in Python 3.
        </td>
    </tr>
    <tr>
        <td>greater than</td>
        <td>
<pre lang="fortran">
>, .gt.
</pre>
        </td>
        <td>
<pre lang="python">
>
</pre>
        </td>
    </tr>
    <tr>
        <td>less than</td>
        <td>
<pre lang="fortran">
<, .lt.
</pre>
        </td>
        <td>
<pre lang="python">
<
</pre>
        </td>
    </tr>
    <tr>
        <td>greater than or equal to</td>
        <td>
<pre lang="fortran">
>=, .ge.
</pre>
        </td>
        <td>
<pre lang="python">
>=
</pre>
        </td>
    </tr>
    <tr>
        <td>less than or equal to</td>
        <td>
<pre lang="fortran">
<=, .ge.
</pre>
        </td>
        <td>
<pre lang="python">
<=
</pre>
        </td>
    </tr>
    <tr>
        <td>array declaration</td>
        <td>
<pre lang="fortran">
real(8), dimension(3) :: a = [1., 2., 3.]
</pre>
        </td>
        <td>
<pre lang="python">
import numpy as np
a = np.array([1., 2., 3.])
</pre>
        </td>
    </tr>
    <tr>
        <td>string array declaration</td>
        <td>
<pre lang="fortran">
character(len=20), dimension(3, 4) :: char_arr
</pre>
        </td>
        <td>
<pre lang="python">
char_arr = np.chararray((3, 4), itemsize=20)
</pre>
        </td>
    </tr>
    <tr>
        <td>elementwise array operations</td>
        <td>
<pre lang="fortran">
a <i>op</i> b
</pre>
<i><code>op</code></i> can be <code>+, -, *, /, **, =, ==</code>, etc.<br>
This is supported since the Fortran 90 standard.
        </td>
        <td>Supported through <code>numpy.ndarray</code> type.</td>
    </tr>
    <tr>
        <td>first element</td>
        <td>
<pre lang="fortran">
a(1)
</pre>
        </td>
        <td>
<pre lang="python">
a[0]
</pre>
        </td>
    </tr>
    <tr>
        <td>slicing</td>
        <td>
<pre lang="fortran">
a(1:5)
</pre>
This slice includes <code>a(5)</code>.
        </td>
        <td>
<pre lang="python">
a[0:5]
</pre>
This slice does not include <code>a[5]</code>.
        </td>
    </tr>
    <tr>
        <td>slicing with steps</td>
        <td>
<pre lang="fortran">
a(1:100:2)
</pre>
        </td>
        <td>
<pre lang="python">
a[0:100:2]
</pre>
        </td>
    </tr>
    <tr>
        <td>size</td>
        <td>
<pre lang="fortran">
size(a)
</pre>
        </td>
        <td>
<pre lang="python">
a.size
</pre>
        </td>
    </tr>
    <tr>
        <td>shape</td>
        <td>
<pre lang="fortran">
shape(a)
</pre>
        </td>
        <td>
<pre lang="python">
a.shape
</pre>
        </td>
    </tr>
    <tr>
        <td>shape along a dimension</td>
        <td>
<pre lang="fortran">
size(a, dim)
</pre>
        </td>
        <td>
<pre lang="python">
a.shape[dim]
</pre>
        </td>
    </tr>
    <tr>
        <td>Type conversion</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>to integer by truncation</td>
        <td>
<pre lang="fortran">
int()
</pre>
        </td>
        <td>
<pre lang="python">
int()
</pre>
        </td>
    </tr>
    <tr>
        <td>to integer by rounding</td>
        <td>
<pre lang="fortran">
nint()
</pre>
        </td>
        <td>
<pre lang="python">
int(round())
</pre>
        </td>
    </tr>
    <tr>
        <td>integer to float</td>
        <td>
<pre lang="fortran">
real(a[, kind])
</pre>
        </td>
        <td>
<pre lang="python">
float()
</pre>
        </td>
    </tr>
    <tr>
        <td>complex to real</td>
        <td>
<pre lang="fortran">
real(z[, kind])
</pre>
        </td>
        <td>
<pre lang="python">
z.real
</pre>
        </td>
    </tr>
    <tr>
        <td>to complex</td>
        <td>
<pre lang="fortran">
cmplx(x [, y [, kind]])
</pre>
        </td>
        <td>
<pre lang="python">
complex()
</pre>
        </td>
    </tr>
    <tr>
        <td>to boolean</td>
        <td>
<pre lang="fortran">
logical()
</pre>
        </td>
        <td>
<pre lang="python">
bool()
</pre>
        </td>
    </tr>
    <tr>
        <td>Derived data types</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>definition</td>
        <td>
<pre lang="fortran">
type Point
    real(8) :: x, y
end type Point
</pre>
        </td>
        <td>
<pre lang="python">
class Point(object):
    def __init__(self, x, y):
        self.x = x
        self.y = y
</pre>
        </td>
    </tr>
    <tr>
        <td>instantiation</td>
        <td>
<pre lang="fortran">
type(Point) :: point1 = Point(-1., 1.)
</pre>
        </td>
        <td>
<pre lang="python">
point1 = Point(-1., 1.)
</pre>
        </td>
    </tr>
    <tr>
        <td>get attributes</td>
        <td>
<pre lang="fortran">
point1%x
point1%y
</pre>
        </td>
        <td>
<pre lang="python">
point1.x
point1.y
</pre>
        </td>
    </tr>
    <tr>
        <td>array of derived type</td>
        <td>
<pre lang="fortran">
type(Point), dimension(:), allocatable :: point_arr
</pre>
        </td>
        <td>No built-in support. You may need to subtype the NumPy array.<br>(Why not use a structured array instead of an array of structure?)</td>
    </tr>
    <tr>
        <td>type bound procedures (aka class method)</td>
        <td>Assume that <code>Circle</code> has a type bound procedure (subroutine) <code>print_area</code>.
<pre lang="fortran">
type(Circle) :: c
call c%print_area
</pre>
        </td>
        <td>Assume that <code>Circle</code> has a class method <code>print_area()</code>.
<pre lang="python">
c = Circle()
c.print_area()
</pre>
        </td>
    </tr>
    <tr>
    <td>Built-in mathematical functions</td>
    <td></td>
    <td></td>
    </tr>
    <tr>
        <td>functions with the same names</td>
        <td>
<pre lang="fortran">
abs(), cos(), cosh(), exp(), floor(), log(),
log10(), max(), min(), sin(), sinh(), sqrt(),
sum(), tan(), tanh()
</pre>
        </td>
        <td>Have the same name in NumPy.
        </td>
    </tr>
    <tr>
        <td>functions with different names</td>
        <td>
<pre lang="fortran">
acos()
aimag()
asin()
atan()
atan2(x, y)
ceiling()
conjg(z)
modulo()
call random_number()
</pre>
        </td>
        <td>
<pre lang="python">
np.arccos()
z.imag
np.arcsin()
np.arctan()
np.arctan2(x, y)
np.ceil()
np.conjugate(z), z.conjugate()
np.mod(), %
np.random.random_sample()
</pre>
        </td>
    </tr>
    <tr>
        <td>Built-in string functions</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>string length</td>
        <td>
<pre lang="fortran">
len()
</pre>
        </td>
        <td>
<pre lang="python">
len()
</pre>
        </td>
    </tr>
    <tr>
        <td>string to ASCII code</td>
        <td>
<pre lang="fortran">
iachar()
</pre>
        </td>
        <td>
<pre lang="python">
ord()
</pre>
        </td>
    </tr>
    <tr>
        <td>ASCII code to string</td>
        <td>
<pre lang="fortran">
achar()
</pre>
        </td>
        <td>
<pre lang="python">
chr()
</pre>
        </td>
    </tr>
    <tr>
        <td>string slicing</td>
        <td>Same as 1D array slicing.</td>
        <td>Same as 1D array slicing.</td>
    </tr>
    <tr>
        <td>find the position of a substring</td>
        <td>
<pre lang="fortran">
index(string, substring)
</pre>
        </td>
        <td>
<pre lang="python">
string.index(substring)
</pre>
        </td>
    </tr>
    <tr>
        <td>string concatenation</td>
        <td>
<pre lang="fortran">
"hello" // "world"
</pre>
        </td>
        <td>
<pre lang="python">
'hello' + 'world'
</pre>
        </td>
    </tr>
    <tr>
        <td>Array constructs</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td><code>where</code> construct</td>
        <td>
<pre lang="fortran">
where a > 0
    b = 0
elsewhere
    b = 1
end where
</pre>
        </td>
        <td>For NumPy arrays,
<pre lang="python">
b[a > 0] = 0
b[a <= 0] - 1
</pre>
For lists, use the higher order function <code>filter()</code> or list comprehension.
        </td>
    </tr>
    <tr>
        <td><code>forall</code> construct</td>
        <td>
<pre lang="fortran">
real, dimension(10, 10) :: a = 0
int :: i, j
...
forall (i = 1:10, j = 1:10, i <= j)
    a(i, j) = i + j
end forall
</pre>
        </td>
        <td>
<pre lang="python">
import itertools
import numpy as np
a = np.zeros((10, 10))
for i, j in itertools.product(range(10), range(10)):
    if i <= j:
        a[i, j] = i + j
</pre>
Note: this is a simple example to reproduce the <code>forall</code> construct in Python. There are definitely other (and more Pythonic) ways of doing the same thing.
        </td>
    </tr>
    <tr>
        <td>Other built-in subroutines</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>CPU time</td>
        <td>
<pre lang="fortran">
call cpu_time()
</pre>
        </td>
        <td>
<pre lang="python">
import time
time.time()
</pre>
        </td>
    </tr>
    <tr>
        <td>command line arguments</td>
        <td>
<pre lang="fortran">
call command_argument_count()
call get_command()
call get_command_argument()
</pre>
        </td>
        <td>For basic parsing, use <code>sys.argv</code>. For more advanced use, see the built-in <code>argparse</code> module.</td>
    </tr>
    <tr>
        <td>Input/output</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>print</td>
        <td>
<pre lang="fortran">
print fmt, <i>&lt;output list&gt;</i>
</pre>
        </td>
        <td>
<pre lang="python">
print()
</pre>
        </td>
    </tr>
    <tr>
        <td>read from the command prompt</td>
        <td>
<pre lang="fortran">
read fmt, <i>&lt;input list&gt;</i>
</pre>
        </td>
        <td>
<pre lang="python">
input(prompt)
</pre>
        </td>
    </tr>
    <tr>
        <td>open a file</td>
        <td>
<pre lang="fortran">
open(unit, file, ...)
</pre>
        </td>
        <td>
<pre lang="python">
f = open(file, mode='r', ...)
</pre>
        </td>
    </tr>
    <tr>
        <td>read from a file</td>
        <td>
<pre lang="fortran">
read(unit, fmt, ...) <i>&lt;input list&gt;</i>
</pre>
        </td>
        <td>
<pre lang="python">
f.read(size)
f.readline()
</pre>
        </td>
    </tr>
    <tr>
        <td>write to a file</td>
        <td>
<pre lang="fortran">
write(unit, fmt, ...) <i>&lt;output list&gt;</i>
</pre>
        </td>
        <td>
<pre lang="python">
f.write()
</pre>
        </td>
    </tr>
    <tr>
        <td>close a file</td>
        <td>
<pre lang="fortran">
close(unit, ...)
</pre>
        </td>
        <td>
<pre lang="python">
f.close()
</pre>
        </td>
    </tr>
    <tr>
        <td>file inquiry</td>
        <td>
<pre lang="fortran">
inquire(unit, ...)
</pre>
        </td>
        <td>Use the file utilities provide by the <code>os</code> module.</td>
    </tr>
    <tr>
        <td>backspace in a file</td>
        <td>
<pre lang="fortran">
backspace(unit, ...)
</pre>
        </td>
        <td>
<pre lang="python">
f.seek(-1, 1)
</pre>
Note: this works only when the file is open as a binary file.
        </td>
    </tr>
    <tr>
        <td>end of file (EOF)</td>
        <td>
<pre lang="fortran">
endfile(unit, ...)
</pre>
        </td>
        <td>
<pre lang="python">
f.read() == ''
</pre>
However, this is generally not needed.
        </td>
    </tr>
    <tr>
        <td>return to the start of a file</td>
        <td>
<pre lang="fortran">
rewind(unit, ...)
</pre>
        </td>
        <td>
<pre lang="python">
f.seek(0)
</pre>
        </td>
    </tr>
</table>
