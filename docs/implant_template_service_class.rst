.. _implant_sops:

Implant Template Query/Retrieve Service Class
=======================================================
The `Implant Template Query/Retrieve Service Class <http://dicom.nema.org/medical/dicom/current/output/html/part04.html#chapter_BB>`_
defines a service that facilitates access to Implant Template objects.

Supported SOP Classes
---------------------

.. _implant_find_sops:

Implant Template Query/Retrieve (Find) SOP Classes
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+-----------------------------+-----------------------------------------------+
| UID                         | SOP Class                                     |
+=============================+===============================================+
| 1.2.840.10008.5.1.4.43.2    | GenericImplantTemplateInformationModelFind    |
+-----------------------------+-----------------------------------------------+
| 1.2.840.10008.5.1.4.44.2    | ImplantAssemblyTemplateInformationModelFind   |
+-----------------------------+-----------------------------------------------+
| 1.2.840.10008.5.1.4.45.2    | ImplantTemplateGroupInformationModelFind      |
+-----------------------------+-----------------------------------------------+


.. _implant_move_sops:

Implant Template Query/Retrieve (Move) SOP Classes
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+-----------------------------+----------------------------------------------+
| UID                         | SOP Class                                    |
+=============================+==============================================+
| 1.2.840.10008.5.1.4.43.3    | GenericImplantTemplateInformationModelMove   |
+-----------------------------+----------------------------------------------+
| 1.2.840.10008.5.1.4.44.3    | ImplantAssemblyTemplateInformationModelMove  |
+-----------------------------+----------------------------------------------+
| 1.2.840.10008.5.1.4.45.3    | ImplantTemplateGroupInformationModelMove     |
+-----------------------------+----------------------------------------------+


.. _implant_get_sops:

Implant Template Query/Retrieve (Get) SOP Classes
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+-----------------------------+---------------------------------------------+
| UID                         | SOP Class                                   |
+=============================+=============================================+
| 1.2.840.10008.5.1.4.43.4    | GenericImplantTemplateInformationModelGet   |
+-----------------------------+---------------------------------------------+
| 1.2.840.10008.5.1.4.44.4    | ImplantAssemblyTemplateInformationModelGet  |
+-----------------------------+---------------------------------------------+
| 1.2.840.10008.5.1.4.45.4    | ImplantTemplateGroupInformationModelGet     |
+-----------------------------+---------------------------------------------+


.. _implant_statuses:

Statuses
--------

.. _implant_find_statuses:

C-FIND Statuses
~~~~~~~~~~~~~~~~

+------------+----------+----------------------------------+
| Code (hex) | Category | Description                      |
+============+==========+==================================+
| 0x0000     | Success  | Success                          |
+------------+----------+----------------------------------+
| 0x0122     | Failure  | SOP Class not supported          |
+------------+----------+----------------------------------+
| 0xFE00     | Cancel   | Processing has been terminated   |
+------------+----------+----------------------------------+

Implant Template Query/Retrieve (Find) Service Statuses
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------------+----------+----------------------------------------------+
| Code (hex)       | Category | Description                                  |
+==================+==========+==============================================+
| 0xA700           | Failure  | Out of resources                             |
+------------------+----------+----------------------------------------------+
| 0xA900           | Failure  | Dataset does not match SOP Class             |
+------------------+----------+----------------------------------------------+
| 0xC000 to 0xCFFF | Failure  | Unable to process                            |
+------------------+----------+----------------------------------------------+
| 0xFF00           | Pending  | Matches are continuing                       |
+------------------+----------+----------------------------------------------+
| 0xFF01           | Pending  | Matches are continuing; one or more Optional |
|                  |          | keys was not supported                       |
+------------------+----------+----------------------------------------------+

pynetdicom Implant Template Query/Retrieve (Find) Statuses
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

When pynetdicom is acting as a Implant Template Query/Retrieve (Find)
SCP it uses the following status codes values to indicate the corresponding
issue has occurred to help aid in debugging.

+------------------+----------+-----------------------------------------------+
| Code (hex)       | Category | Description                                   |
+==================+==========+===============================================+
| 0xC001           | Failure  | User's callback implementation returned a     |
|                  |          | status Dataset with no (0000,0900) *Status*   |
|                  |          | element                                       |
+------------------+----------+-----------------------------------------------+
| 0xC002           | Failure  | User's callback implementation returned an    |
|                  |          | invalid status object (not a pydicom Dataset  |
|                  |          | or an int)                                    |
+------------------+----------+-----------------------------------------------+
| 0xC310           | Failure  | Failed to decode the dataset received from    |
|                  |          | the peer                                      |
+------------------+----------+-----------------------------------------------+
| 0xC311           | Failure  | Unhandled exception raised by the user's      |
|                  |          | implementation of the ``on_c_find`` callback  |
+------------------+----------+-----------------------------------------------+
| 0xC312           | Failure  | Failed to encode the dataset received from    |
|                  |          | the user's implementation of the ``on_c_find``|
|                  |          | callback                                      |
+------------------+----------+-----------------------------------------------+


.. _implant_get_statuses:

C-GET Statuses
~~~~~~~~~~~~~~

+------------+----------+----------------------------------+
| Code (hex) | Category | Description                      |
+============+==========+==================================+
| 0x0000     | Success  | Success                          |
+------------+----------+----------------------------------+
| 0x0122     | Failure  | SOP Class not supported          |
+------------+----------+----------------------------------+
| 0x0124     | Failure  | Not authorised                   |
+------------+----------+----------------------------------+
| 0x0210     | Failure  | Duplicate invocation             |
+------------+----------+----------------------------------+
| 0x0212     | Failure  | Mistyped argument                |
+------------+----------+----------------------------------+
| 0xFE00     | Cancel   | Sub-operations terminated        |
+------------+----------+----------------------------------+

Implant Template Query/Retrieve (Get) Service Statuses
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------------+----------+----------------------------------------------+
| Code (hex)       | Category | Description                                  |
+==================+==========+==============================================+
| 0xA701           | Failure  | Out of resources; unable to calculate number |
|                  |          | of matches                                   |
+------------------+----------+----------------------------------------------+
| 0xA702           | Failure  | Out of resources; unable to perform          |
|                  |          | sub-operations                               |
+------------------+----------+----------------------------------------------+
| 0xA900           | Failure  | Dataset does not match SOP Class             |
+------------------+----------+----------------------------------------------+
| 0xB000           | Warning  | Sub-operations complete, one or more         |
|                  |          | or warnings                                  |
+------------------+----------+----------------------------------------------+
| 0xC000 to 0xCFFF | Failure  | Unable to process                            |
+------------------+----------+----------------------------------------------+
| 0xFF00           | Pending  | Sub-operations are continuing                |
+------------------+----------+----------------------------------------------+

pynetdicom Implant Template Query/Retrieve (Get) Statuses
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------------+----------+-----------------------------------------------+
| Code (hex)       | Category | Description                                   |
+==================+==========+===============================================+
| 0xC001           | Failure  | User's callback implementation returned a     |
|                  |          | status Dataset with no (0000,0900) *Status*   |
|                  |          | element                                       |
+------------------+----------+-----------------------------------------------+
| 0xC002           | Failure  | User's callback implementation returned an    |
|                  |          | invalid status object (not a pydicom Dataset  |
|                  |          | or an int)                                    |
+------------------+----------+-----------------------------------------------+
| 0xC410           | Failure  | Failed to decode the dataset received from    |
|                  |          | the peer                                      |
+------------------+----------+-----------------------------------------------+
| 0xC411           | Failure  | Unhandled exception raised by the user's      |
|                  |          | implementation of the ``on_c_get`` callback   |
+------------------+----------+-----------------------------------------------+
| 0xC413           | Failure  | The user's implementation oc the ``on_c_get`` |
|                  |          | callback yielded an invalid number of         |
|                  |          | sub-operations                                |
+------------------+----------+-----------------------------------------------+


.. _implant_move_statuses:

C-MOVE Statuses
~~~~~~~~~~~~~~~

+------------+----------+----------------------------------+
| Code (hex) | Category | Description                      |
+============+==========+==================================+
| 0x0000     | Success  | Success                          |
+------------+----------+----------------------------------+
| 0x0122     | Failure  | SOP Class not supported          |
+------------+----------+----------------------------------+
| 0x0124     | Failure  | Not authorised                   |
+------------+----------+----------------------------------+
| 0x0210     | Failure  | Duplicate invocation             |
+------------+----------+----------------------------------+
| 0x0211     | Failure  | Unrecognised operation           |
+------------+----------+----------------------------------+
| 0x0212     | Failure  | Mistyped argument                |
+------------+----------+----------------------------------+
| 0xFE00     | Cancel   | Sub-operations terminated        |
+------------+----------+----------------------------------+

Implant Template Query/Retrieve (Move) Service Statuses
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------------+----------+----------------------------------------------+
| Code (hex)       | Category | Description                                  |
+==================+==========+==============================================+
| 0xA701           | Failure  | Out of resources; unable to calculate number |
|                  |          | of matches                                   |
+------------------+----------+----------------------------------------------+
| 0xA702           | Failure  | Out of resources; unable to perform          |
|                  |          | sub-operations                               |
+------------------+----------+----------------------------------------------+
| 0xA801           | Failure  | Move destination unknown                     |
+------------------+----------+----------------------------------------------+
| 0xA900           | Failure  | Dataset does not match SOP Class             |
+------------------+----------+----------------------------------------------+
| 0xB000           | Warning  | Sub-operations complete, one or more         |
|                  |          | or warnings                                  |
+------------------+----------+----------------------------------------------+
| 0xC000 to 0xCFFF | Failure  | Unable to process                            |
+------------------+----------+----------------------------------------------+
| 0xFF00           | Pending  | Sub-operations are continuing                |
+------------------+----------+----------------------------------------------+

pynetdicom Implant Template Query/Retrieve (Move) Statuses
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------------+----------+-----------------------------------------------+
| Code (hex)       | Category | Description                                   |
+==================+==========+===============================================+
| 0xC001           | Failure  | User's callback implementation returned a     |
|                  |          | status Dataset with no (0000,0900) *Status*   |
|                  |          | element                                       |
+------------------+----------+-----------------------------------------------+
| 0xC002           | Failure  | User's callback implementation returned an    |
|                  |          | invalid status object (not a pydicom Dataset  |
|                  |          | or an int)                                    |
+------------------+----------+-----------------------------------------------+
| 0xC510           | Failure  | Failed to decode the dataset received from    |
|                  |          | the peer                                      |
+------------------+----------+-----------------------------------------------+
| 0xC511           | Failure  | Unhandled exception raised by the user's      |
|                  |          | implementation of the ``on_c_get`` callback   |
+------------------+----------+-----------------------------------------------+
| 0xC513           | Failure  | The user's implementation oc the ``on_c_move``|
|                  |          | callback yielded an invalid number of         |
|                  |          | sub-operations                                |
+------------------+----------+-----------------------------------------------+
| 0xC514           | Failure  | The user's implementation oc the ``on_c_move``|
|                  |          | callback failed to yield the (address, port)  |
|                  |          | and/or the number of sub-operations           |
+------------------+----------+-----------------------------------------------+
| 0xC515           | Failure  | The user's implementation oc the ``on_c_move``|
|                  |          | callback failed to yield a valid (address,    |
|                  |          | port) pair                                    |
+------------------+----------+-----------------------------------------------+


References
----------

* DICOM Standard, Part 4, `Annex C <http://dicom.nema.org/medical/dicom/current/output/html/part04.html#chapter_C>`_
* DICOM Standard, Part 4, `Annex BB <http://dicom.nema.org/medical/dicom/current/output/html/part04.html#chapter_BB>`_
* DICOM Standard, Part 7, Sections
  `9.1.2.1.5 <http://dicom.nema.org/medical/dicom/current/output/chtml/part07/chapter_9.html#sect_9.1.2.1.5>`_,
  `9.1.3.1.6 <http://dicom.nema.org/medical/dicom/current/output/chtml/part07/chapter_9.html#sect_9.1.3.1.6>`_ and
  `9.1.4.1.7 <http://dicom.nema.org/medical/dicom/current/output/chtml/part07/chapter_9.html#sect_9.1.4.1.7>`_
