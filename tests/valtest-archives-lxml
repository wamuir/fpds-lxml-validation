#!/usr/bin/env python3

import io
from lxml import etree


ns = {'ns1': 'https://www.fpds.gov/FPDS'}

''' lxml validation of records within award archive '''

with open("../sample-data/1100-EXECUTIVEOFFICEOFTHEPRESIDENT-AWARD.xml",
          "rb") as f1:
    xml = etree.parse(io.BytesIO(f1.read()))

with open("../FPDS/schema/DataCollection/contracts/1.5/Award.xsd", "rb") as f2:
    xmlschema_parsed = etree.parse(io.BytesIO(f2.read()))
    xmlschema = etree.XMLSchema(xmlschema_parsed)

awdval = [xmlschema.validate(a) for a in xml.xpath('ns1:award', namespaces=ns)]
print('Award archive validated:', all(awdval))


''' lxml validation of records within IDV archive '''

with open("../sample-data/1100-EXECUTIVEOFFICEOFTHEPRESIDENT-IDV.xml",
          "rb") as f3:
    xml = etree.parse(io.BytesIO(f3.read()))

with open("../FPDS/schema/DataCollection/contracts/1.5/IDV.xsd", "rb") as f4:
    xmlschema_parsed = etree.parse(io.BytesIO(f4.read()))
    xmlschema = etree.XMLSchema(xmlschema_parsed)

idvval = [xmlschema.validate(i) for i in xml.xpath('ns1:IDV', namespaces=ns)]
print('IDV archive validated:', all(idvval))

