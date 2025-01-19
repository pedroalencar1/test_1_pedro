# How to build a package

Pedro Alencar
08.01.2025

**1. Install some packages**

```pip install setuptools wheel twine```

**2. Create a local folder**

```
Your_Package/
+--Your_Package/
|  +-- __init__.py
|  +-- module1.py
+-- setup.py
+-- README.md
+-- tests/

```

_NOTE: the package name should not be short (e.g. test), simple (e.g. my_package), or claimed (e.g. numpy)_


* the file `__init__.py` tells python this folder should be treated as a package
* the file `module1.py` contains some functions
* the file `setup.py` will contain all information to build your package
* `README.md` cotains general information and description of your package
* `tests\` is a folder where you can test your code


**3. setup.py file**

```
from setuptools import setup, find_packages

with open('README.md', 'r') as f:
    description = f.read()

setup(

    name= "Your_Package",
    version= "0.0.1",
    packages=find_packages(), install_requires=[
        # Add dependencies here.
        # e.g. 'numpy >= 1.11.1'
    ],
    long_description=description,
    long_description_content_type='text/markdown',
)

```

**4. Run the setup.py file and build the package locally**

_Open a terminal at the project locatior or use the VSCode terminal_ 

run: `python setup.py sdist bdist_wheel`

then build: `pip install .` or `pip install [whell filename]`
	
_the whell filename is created after the setup.py build and is the file dist/*.whl_


**5. Publishing your package**

You can publish your package on Github as we did in the last class. However, users would need to build the pakcages themselves. Another way is to publish is at `PYPI` which allows your package to be installed with `pip`

* create an account at [pypi.org](pypi.org) and validate your email.
* at 'Account Settings -> API Tokens', create a token
* in your home directory ($HOME) create a file `.pypirc`

	**- in the .pypirc file, write:**

```
[pypi]
  username = __token__
  password = [your pypi token]
```

* once your token is set, you are authorized to publish your package at PYPI

	run: `twine upload dist/*`



































