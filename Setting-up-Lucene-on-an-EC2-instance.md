Follow the instructions below to setup Lucene on your EC2 instance.

1. Install and setup Java on EC2. I installed Java-8 but you free to choose the version you want. [This](https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-get-on-ubuntu-16-04) link gives detailed instructions on how to install it and set the appropriate environment variables for Ubuntu 16.04.

2. Download the latest version of pylucene from [this](http://lucene.apache.org/pylucene/install.html) link.

3. Unzip the tar file in the location you want. Considering you downloaded the latest Pylucene version, this should create a folder named **pylucene-6.2.0**.

4. Navigate to the location **$/pylucene-6.2.0/jcc**.

5. Run the command **`python setup.py build`**

6. Post this run **`sudo python setup.py install`**

7. Go back to **$/pylucene-6.2.0/** and open the **Makefile** present there for editing.

8. In the Makefile, uncomment the portion for **Linux** and replace the variable value for **JCC** to the value **`$/pylucene-6.2.0/jcc/jcc/__init__.py`**. The entry should look something like this:

```
# Linux (Ubuntu 6.06, Python 2.4, Java 1.5, no setuptools)
PREFIX_PYTHON=/usr
ANT=ant
PYTHON=$(PREFIX_PYTHON)/bin/python
JCC=$(PYTHON) /home/ubuntu/pylucene-6.2.0/jcc/jcc/__init__.py
NUM_FILES=8
```
9. Run the command **`````make`````**

10. Run the command **`````make test`````**

11. Run **`````sudo make install`````**

You are all set. You can check if lucene and java are installed properly by running the following python lines:

```
#Following 4 imports should work to show proper links between lucene and java
from jcc import _jcc
import lucene
from java.nio.file import Paths 
from org.apache.lucene.analysis.standard import StandardAnalyzer

lucene.initVM()
```


