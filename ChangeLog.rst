4.2.3
-----
* Fix `pyarmor-webui` can not start issue
* Fix `runtime-path` issue in webui
* Rename platform name `macosx_intel` to `macosx_x86_64` (#36)

4.2.2
-----
* Fix webui import error.

4.2.1
-----
* Add option `--recursive` for command `obfuscate`

4.1.4
-----
* Rewrite project long description.

4.1.3
-----
* Fix Python3 issue for `get_license_info`

4.1.2
-----
* Add function `get_license_info` in `pytransform.py` to show license information

4.1.1
-----
* Fix import `main` from `pyarmor` issue

4.0.3
-----
* Add command `capsule`
* Find default capsule in the current path other than `--src` in command `obfuscate`
* Fix pip install issue #30

4.0.2
-----
* Rename `pyarmor.py` to `pyarmor-depreted.py`
* Rename `pyarmor2.py` to `pyarmor.py`
* Add option `--capsule`, `-disable-restrict-mode` and `--output` for command `licenses`

4.0.1
-----
* Add option `--capsule` for command `init`, `config` and `obfuscate`
* Deprecate option `--clone` for command `init`, use `--capsule` instead
* Fix `sys.settrace` and `sys.setprofile` issues for auto-wrap mode

3.9.9
-----
* Fix segmentation fault issues for `asyncio`, `typing` modules

3.9.8
-----
* Add documentation for examples (examples/README.md)

3.9.7
-----
* Fix windows 10 issue: access violation reading 0x000001ED00000000

3.9.6
-----
* Fix the generated license bind to fixed machine in webui is not correct
* Fix extra output path issue in webui

3.9.5
-----
* Show registration code when printing version information

3.9.4
-----
* Rewrite long description of package in pypi

3.9.3
-----
* Fix issue: `__file__` is not really path in main code of module when import obfuscated module

3.9.2
-----
* Replace option `--disable-restrict-mode` with `--no-restrict` in command `obfuscate`
* Add option `--title` in command `config`
* Change the output path of entry scripts when entry scripts belong to package
* Refine document `user-guide.md` and `mechanism.md`

3.9.1
-----
* Add option `--type` for command `init`
* Refine document `user-guide.md` and `mechanism.md`

3.9.0
-----
This version introduces a new way `auto-wrap` to protect python code when it's imported by outer scripts.

Refer to [Mechanism Without Restrict Mode](src/mechanism.md#mechanism-without-restrict-mode)

* Add new mode `wrap` for `--obf-code-mode`
* Remove `func.__refcalls__` in `__wraparmor__`
* Add new project attribute `is_package`
* Add option `--is-package` in command `config`
* Add option `--disable-restrict-mode` in command `obfuscate`
* Reset `build_time` when project configuration is changed
* Change output path when `is_package` is set in command `build`
* Change default value of project when find `__init__.py` in comand `init`
* Project attribute `entry` supports absolute path

3.8.10
------
* Fix shared code object issue in `__wraparmor__`

3.8.9
-----
* Clear frame as long as `tb` is not `Py_None` when call `__wraparmor__`
* Generator will not be obfucated in `__wraparmor__`

3.8.8
-----
* Fix bug: the `frame.f_locals` still can be accessed in callback function

3.8.7
-----
* The `frame.f_locals` of `wrapper` and wrapped function will return an empty dictionary once `__wraparmor__` is called.

3.8.6
-----
* The `frame.f_locals` of `wrapper` and wrapped function return an empty dictionary, all the other frames still return original value.

3.8.5
-----
* The `frame.f_locals` of all frames will always return an empty dictionary to protect runtime data.
* Add extra argument `tb` when call `__wraparmor__` in decorator `wraparmor`, pass None if no exception.

3.8.4
-----
* Do not touch `frame.f_locals` when raise exception, let decorator `wraparmor` to control everything.

3.8.3
-----
* Fix issue: option `--disable-restrict-mode` doesn't work in command `licenses`
* Remove freevar `func` from `frame.f_locals` when raise exception in decorator `wraparmor`

3.8.2
-----
* Change module filename to `<frozen modname>` in traceback, set attribute `__file__` to real filename when running obfuscated scripts.

3.8.1
-----
* Try to access original func_code out of decorator `wraparmor` is forbidden.

3.8.0
-----
* Add option `--output` for command `build`, it will override the value in project configuration file.
* Fix issue: defalut project output path isn't relative to project path.
* Remove extra file "product.key" after obfuscating scripts.

3.7.5
-----
* Remove dotted name from filename in traceback, if it's not a package.

3.7.4
-----
* Strip `__init__` from filename in traceback, replace it with package name.

3.7.3
-----
* Remove brackets from filename in traceback, and add dotted prefix.

3.7.2
-----
* Change filename in traceback to `<frozen [modname]>`, other than original filename

3.7.1
-----
* Fix issue #12: module attribute `__file__` is filename in build machine other than filename in target machine.
* Builtins function `__wraparmor__` only can be used in the decorator `wraparmor`

3.7.0
-----
* Fix issue #11: use decorator "wraparmor" to obfuscate func_code as soon as function returns.
* Document usage of decorator "wraparmor",  refer to **src/user-guide.md#use-decorator-to-protect-code-objects-when-disable-restrict-mode**

3.6.2
-----
* Fix issue #8 (Linux): option --manifest broken in shell script

3.6.1
-----
* Add option "Restrict Mode" in web ui
* Document restrict mode in details (user-guide.md)

3.6.0
-----
* Introduce restrict mode to avoid obfuscated scripts observed from no obfuscated scripts
* Add option --disable-restrict-mode for command "config"

3.5.1
-----
* Support pip install pyarmor

3.5.0
-----
* Fix Python3.6 issue: can not run obfuscated scripts, because it uses a 16-bit wordcode instead of bytecode
* Fix Python3.7 issue: it adds a flag in pyc header
* Fix option --obf-module-mode=none failed
* Add option --clone for command "init"
* Generate runtime files to separate path “runtimes" when project runtime-path is set
* Add advanced usages in user-guide

3.4.3
-----
* Fix issue: raise exception when project entry isn't obfuscated

3.4.2
-----
* Add webui to manage project

3.4.1
-----
* Fix README.rst format error.
* Add title attribute to project
* Print new command help when option is -h, --help

3.4.0
-----
Pyarmor v3.4 introduces a group new commands. For a simple package,
use command **obfuscate** to obfuscate scripts directly. For
complicated package, use Project to manage obfuscated scripts.

Project includes 2 files, one configure file and one project
capsule. Use manifest template string, same as MANIFEST.in of Python
Distutils, to specify the files to be obfuscated.

To create a project, use command **init**, use command **info** to
show project information. **config** to update project settings, and
**build** to obfuscate the scripts in the project.

Other commands, **benchmark** to metric performance, **hdinfo** to
show hardware information, so that command **licenses** can generate
license bind to fixed machine.

All the old commands **capsule**, **encrypt**, **license** are
deprecated, and will be removed from v4.

A new document [src/user-guide.md](src/user-guide.md) is written for
this new version.

3.3.1
-----
* Remove unused files in distribute package

3.3.0
-----
In this version, new obfuscate mode 7 and 8 are introduced. The main
difference is that obfuscated script now is a normal python file (.py)
other than compiled script (.pyc), so it can be used as common way.

Refer to https://github.com/dashingsoft/pyarmor/blob/v3.3.0/src/mechanism.md

* Introduce new mode: 7, 8
* Change default mode from 3 to 8
* Change benchmark.py to test new mode
* Update webapp and tutorial
* Update usage
* Fix issue of py2exe, now py2exe can work with python scripts obfuscated by pyarmor
* Fix issue of odoo, now odoo can load python modules obfuscated by pyarmor

3.2.1
-----
* Fix issue: the traceback of an exception contains the name "<pytransform>" instead of the correct module name
* Fix issue: All the constant, co_names include function name, variable name etc still are in clear text.
  Refer to https://github.com/dashingsoft/pyarmor/issues/5

3.2.0
-----
From this version, a new obfuscation mode is introduced. By this way,
no import hooker, no setprofile, no settrace required. The performance
of running or importing obfuscation python scripts has been remarkably
improved. It's significant for Pyarmor.

* Use this new mode as default way to obfuscate python scripts.
* Add new script "benchmark.py" to check performance in target machine: python benchmark.py
* Change option "--bind-disk" in command "license",  now it must be have a value

3.1.7
-----
* Add option "--bind-mac", "--bind-ip", "--bind-domain" for command "license"
* Command "hdinfo" show more information(serial number of hdd, mac address, ip address, domain name)
* Fix the issue of dev name of hdd for Banana Pi

3.1.6
-----
* Fix serial number of harddisk doesn't work in mac osx.

3.1.5
-----
* Support MACOS

3.1.4
-----
* Fix issue: load _pytransfrom failed in linux x86_64 by subprocess.Popen
* Fix typo in error messge when load _pytransfrom failed.

3.1.3
-----
A web gui interface is introduced as Pyarmor WebApp， and support MANIFEST.in

* In encrypt command, save encrypted scripts with same file structure of source.
* Add a web gui interface for pyarmor.
* Support MANIFEST.in to list files for command encrypt
* Add option --manifest, file list will be written here
* DO NOT support absolute path in file list for command encrypt
* Option --main support format "NAME:ALIAS.py"

3.1.2
-----
* Refine decrypted mechanism to improve performance
* Fix unknown opcode problem in recursion call
* Fix wrapper scripts generated by -m in command 'encrypt' doesn't work
* Raise ImportError other than PytransformError when import encrypted module failed

3.1.1
-----
In this version, introduce 2 extra encrypt modes to improve
performance of encrypted scripts.

* Fix issue when import encrypted package
* Add encrypted mode 2 and 3 to improve performance
* Refine module pyimcore to improve performance

3.0.1
-----
It's a milestone for Pyarmor, from this version, use ctypes import
dynamic library of core functions, other than by python extensions
which need to be built with every python version.

Besides, in this version, a big change which make Pyarmor could avoid
soure script got by c debugger.

* Use ctypes load core library other than python extentions which need
  built for each python version.
* "\__main__" block not running in encrypted script.
* Avoid source code got by c debugger.
* Change default outoupt path to "build" in command "encrypt"
* Change option "--bind" to "--bind-disk" in command "license"
* Document usages in details

2.6.1
-----
* Fix encrypted scripts don't work in multi-thread framework (Django).

2.5.5
-----
* Add option '-i' for command 'encrypt' so that the encrypted scripts will be saved in the original path.

2.5.4
-----
* Verbose tracelog when checking license in trace mode.
* In license command, change default output filename to "license.lic.txt".
* Read bind file when generate license in binary mode other than text mode.

2.5.3
-----
* Fix problem when script has line "from __future__ import with_statement"
* Fix error when running pyarmor by 32bit python on the 64bits Windows.
* (Experimental)Support darwin_15-x86_64 platform by adding extensions/pytransform-2.3.3.darwin_15.x86_64-py2.7.so

2.5.2
-----
* License file can mix expire-date with fix file or fix key.
* Fix log error: not enough arguments for format string

2.5.1
-----
* License file can bind to ssh private key file or any other fixed file.

2.4.1
-----
* Change default extension ".pyx" to ".pye", because it confilcted with CPython.
* Custom the extension of encrypted scripts by os environment variable: PYARMOR_EXTRA_CHAR
* Block the hole by which to get bytescode of functions.

2.3.4
-----
* The trial license will never be expired (But in trial version, the
  key used to encrypt scripts is fixed).

2.3.3
-----
* Refine the document

2.3.2
-----
* Fix error data in examples of wizard

2.3.1
-----
* Implement Run function in the GUI wizard
* Make license works in trial version

2.2.1
-----
* Add a GUI wizard
* Add examples to show how to use pyarmor

2.1.2
-----
* Fix syntax-error when run/import encrypted scripts in linux x86_64

2.1.1
-----
* Support armv6

2.0.1
-----
* Add option '--path' for command 'encrypt'
* Support script list in the file for command 'encrypt'
* Fix issue to encrypt an empty file result in pytransform crash

1.7.7
-----

* Add option '--expired-date' for command 'license'
* Fix undefined 'tfm_desc' for arm-linux
* Enhance security level of scripts

1.7.6
-----

* Print exactaly message when pyarmor couldn't load extension
  "pytransform"

* Fix problem "version 'GLIBC_2.14' not found"

* Generate "license.lic" which could be bind to fixed machine.

1.7.5
-----

* Add missing extensions for linux x86_64.

1.7.4
-----

* Add command "licene" to generate more "license.lic" by project
  capsule.

1.7.3
-----

* Add information for using registration code

1.7.2
-----

* Add option --with-extension to support cross-platform publish.
* Implement command "capsule" and add option --with-capsule so that we
  can encrypt scripts with same capsule.
* Remove command "convert" and option "-K/--key"

1.7.1
-----

* Encrypt pyshield.lic when distributing source code.

1.7.0
-----

* Enhance encrypt algorithm to protect source code.
* Developer can use custom key/iv to encrypt source code
* Compiled scripts (.pyc, .pyo) could be encrypted by pyshield
* Extension modules (.dll, .so, .pyd) could be encrypted by pyshield
